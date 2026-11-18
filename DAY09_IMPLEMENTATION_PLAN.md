# Kế hoạch triển khai Day-09

1. Ghép `src` chính thức của Day-08 vào project và kiểm tra shape tham chiếu baseline.
2. Tạo eval set v1 và nhãn; gắn mã FM-01..FM-09 cùng provenance dựa trên trace.
3. Cài đặt confusion matrix, precision/recall, Cohen's kappa, Rogan–Gladen, paired bootstrap, pass@k và pass^k.
4. Cài đặt grader approval, số tiền hoàn và tính nhất quán reply/ledger; thêm metric FM-08.
5. Cài đặt integrity gate, threshold ratchet và slice checks.
6. Cấu hình mapping adversarial v2, các slice money/adversarial và ngưỡng pass^5.
7. Chạy smoke, toàn bộ test, eval report, gate fixed/regression, mutation scorecard và traps.
8. Ghi kết quả thực tế và giới hạn vào test report và status log.

Output dự kiến gồm `data/eval/eval_set_v1.jsonl`, `labels_v1.json`, các file tương ứng của v2, baseline/evaluation JSON report và bằng chứng test/gate sạch. Report phải được sinh bằng các lệnh có sẵn, không được sửa tay.
