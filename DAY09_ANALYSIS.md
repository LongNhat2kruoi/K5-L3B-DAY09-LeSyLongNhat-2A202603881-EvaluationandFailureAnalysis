# Phân tích Day-09

Day-08 cung cấp agent hoàn tiền LogiX-VN chạy offline, MockLLM, bốn kiến trúc, host xử lý policy/approval, độ bền SQLite, handoff an toàn, trace và bộ test public. Ranh giới quan trọng là code chịu trách nhiệm về tiền, approval, phân quyền và idempotency; model chỉ diễn giải và soạn nội dung.

Day-09 đánh giá agent kế thừa thay vì thay đổi hành vi của nó. Day-09 bổ sung eval set tách nhãn khỏi item, taxonomy lỗi, thống kê hiệu chỉnh judge, grader theo trajectory/outcome, release gate bằng paired bootstrap, các slice adversarial, pass@k/pass^k và kiểm tra integrity chống làm sai lệch kết quả đánh giá.

Source Day-09 được ghép từ `src/lab8` chính thức của Day-08 và `src/lab9`. Dữ liệu và cấu hình Day-08 được tái sử dụng nguyên trạng. Day-09 chỉ thay đổi code đánh giá, cấu hình đánh giá và tài liệu; không sửa policy host hay durability của Lab 8.

Các thành phần tái sử dụng: `lab8.benchmark.run_trial`, `lab8.metrics`, `lab8.db`, trace events, MockLLM và swarm tham chiếu. Thành phần mới: `lab9.evalset`, `stats`, `graders`, `gate`, `variants`, `mutation` và `traps`.

Ràng buộc gồm: chạy offline và tái lập được, seed cố định 11/22/33/44/55, nhãn nằm ngoài item, không sửa tay report, và chặn release khi có vi phạm an toàn hoặc hồi quy năng lực có ý nghĩa thống kê.
