# Báo cáo kiểm thử Day-09

## Kiểm thử và xác nhận

Đã thực hiện sau khi triển khai:

- `python -m lab9.smoke`
- `python -m pytest -q -m student -o addopts=`
- `python -m lab9.evalset --build --check`
- build/check eval set v2
- đánh giá baseline, fixed và seeded-regression cùng các gate
- mutation scorecard và public trap suite

Kết quả thực tế: `lab9.smoke` PASS; bộ test Day-09 đạt `23 passed, 3 deselected`; eval set v1 và v2 đều báo `0 problem(s)`. Hiệu chỉnh tone judge đạt P=0.857, R=0.800, κ=0.757 và vượt ngưỡng; helpful judge bị loại vì κ=0.375, R=0.300.

Baseline v1 có pass_rate 0.9857 và pass_5 0.9286. `fixed` được phép merge (exit 0). `seeded_regression` bị chặn (exit 1), pass_rate 0.7143 và CI [-0.500, -0.057]. Mutation score nâng cao đạt 3/3, không có false alarm. Cả bốn public trap đều bị chặn; lệnh trap exit 0. A/A delta giữa các seed thay thế là 0.0000. Grader detection đạt 100%, false alarm 0%.

Lần chạy đầu bị lỗi vì chưa cài `pydantic-evals`; cài `requirements-lab9.txt` đã khắc phục môi trường. Cảnh báo còn lại là pytest chưa nhận marker `student`, do bản checkout độc lập này không chứa cấu hình pytest gốc của Lab-8.

## Giới hạn

Đánh giá chạy offline, sử dụng MockLLM, 14 item public cùng adversarial pack v2 và nhãn judge replay. Kết quả chưa chứng minh hiệu năng production hoặc độ tin cậy của judge trên tập người dùng mới. Năm seed không đủ để phát hiện ổn định lỗi chỉ xuất hiện ở một trong ba lần chạy.
