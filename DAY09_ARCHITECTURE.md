# Kiến trúc Day-09

```text
Day-8 world + claims -> evalset items + external labels
                       -> lab9.eval -> Lab-8 shape -> SQLite + trace
                                     -> code graders -> rows -> metrics
                       -> gate: integrity -> thresholds -> paired CI -> slices
```

Harness chạy một SQLite store độc lập cho mỗi item/seed. Mỗi trial trả về kết quả Day-08, snapshot ledger, trace events và artifact blob. Code grader kiểm tra các output này mà không chạy lại model. Report tổng hợp số lỗi an toàn, tỷ lệ outcome, pass^5, chi phí và trung bình theo item.

Judge replay được hiệu chỉnh riêng bằng confusion statistics và kappa. Vì tiền và approval là các sự kiện an toàn xác định được, chúng luôn do code grader chấm. Release gate trước hết loại report không hữu hạn, thiếu dòng, trùng dòng, đổi nhãn hoặc bị evaluator failure; sau đó áp dụng ngưỡng metric và kiểm tra paired bootstrap không suy giảm. v2 bổ sung gate theo slice và ratchet để ngăn việc nới lỏng spec trên cùng phiên bản eval set.

Các variant đăng ký những hồi quy có kiểm soát trên cùng host Day-08. Mutation và trap suite xác minh gate phát hiện hồi quy thật, đồng thời từ chối report bị bỏ dòng, chọn seed có lợi, chứa NaN hoặc dùng spec bị nới lỏng.
