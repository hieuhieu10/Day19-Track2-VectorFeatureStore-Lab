# Reflection — Lab 19

**Tên:** _<Họ Tên>_
**Cohort:** _<A20-K1 / A20-K2 / ...>_
**Path đã chạy:** _lite_

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Trên golden set 50 queries, **BM25** thắng rõ ở `exact` queries vì các từ khóa kỹ
thuật xuất hiện gần như nguyên văn trong corpus, nên match lexical rất mạnh
(96.7%). `paraphrase` là loại khó nhất trong lab này: cả BM25 lẫn vector đều
giảm, nhưng BM25 vẫn hơi nhỉnh hơn semantic trên bộ dữ liệu hiện tại
(33.3% vs 24.0%) vì embedding `bge-small-en-v1.5` chưa tối ưu cho tiếng Việt.
Với `mixed` queries, **hybrid** thắng rõ nhất (100.0%) vì nó tận dụng được cả
tín hiệu exact term của BM25 và tín hiệu ngữ nghĩa của vector search. Trung
bình toàn bộ, hybrid đạt cao nhất (78.6%).

Mình **không dùng hybrid** khi bài toán quá đơn giản hoặc có ràng buộc rất rõ.
Nếu query là exact lookup, danh mục nhỏ, cần latency thấp nhất thì BM25 là đủ.
Nếu dữ liệu nhiều paraphrase đa ngôn ngữ và embedding mạnh, semantic-only có
thể hợp lý hơn để giảm độ phức tạp hệ thống.

---

## Điều ngạc nhiên nhất khi làm lab này

Điều ngạc nhiên nhất là hybrid không phải lúc nào cũng thắng từng loại query,
nhưng lại thắng tốt nhất ở mức tổng thể vì nó ổn định hơn trước nhiều kiểu truy vấn.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
