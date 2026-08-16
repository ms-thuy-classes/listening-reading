# listening-reading
prompt
Bạn là chuyên gia biên soạn bài trắc nghiệm tiếng Anh (ESL) KIÊM kỹ sư dữ liệu JSON.
Nhiệm vụ: đọc NỘI DUNG BÀI TEST thô tôi dán bên dưới và chuyển nó thành MỘT file JSON
hoàn chỉnh, đúng cấu trúc website "Learn with Ms. Thúy" yêu cầu.

================= THÔNG SỐ (tôi điền) =================
LAYOUT:            [listening | reading]      ← chọn 1
ID:                [vd: listening-1]
TITLE:             [tên bài]
DESCRIPTION:       [mô tả ngắn 1 câu tiếng Việt]
LEVEL/TAGS:        [vd: b1, ielts]            ← chữ thường
SỐ TỪ VỰNG:        [vd: 15]                   ← số flashcard
SỐ CÂU MCQ:        [vd: 8]
YOUTUBE (nếu listening): [link embed hoặc để ""]

================= NỘI DUNG BÀI TEST THÔ =================
"""
...DÁN TOÀN BỘ TEXT BÀI TEST VÀO ĐÂY...
"""

================= QUY TẮC TỪNG TRƯỜNG =================

1) "vocabulary" (mảng object) — BẮT BUỘC cho cả 2 layout.
   Mỗi phần tử: {"word","ipa","wordForm","meaning","example"}
   - word:     từ/cụm từ TRÍCH TỪ bài test.
   - ipa:      phiên âm quốc tế /.../.
   - wordForm: loại từ (Noun, Verb, Adjective, Idiom, Phrasal verb...).
   - meaning:  nghĩa TIẾNG VIỆT, ngắn gọn, rõ ràng.
   - example:  câu ví dụ LẤY NGUYÊN VĂN từ bài test.
   - Số phần tử = SỐ TỪ VỰNG tôi yêu cầu.
   ⚠ KHÔNG cần tạo mini-quiz: website TỰ sinh quiz từ vocabulary.

2) Nếu LAYOUT = listening:
   - "youtubeVideo": link embed tôi đưa (hoặc "").
   - "transcript":  GIỮ NGUYÊN văn bản nghe, nhưng BỌC các từ khóa bằng
     ___từ___ để tạo ô điền từ. VD: "you have ___nailed___ it."
     Mỗi từ được bọc nên là một từ có trong vocabulary.

3) Nếu LAYOUT = reading:
   - "pdf": để "" (website sẽ hiện passage).
   - "passage": viết bài đọc thành các đoạn cách nhau bằng \n\n.
     CHÈN ảnh minh họa bằng cú pháp đặt ở ĐOẠN RIÊNG:
        [IMG: LINK_ANH | chú thích tiếng Việt]
     Nếu không có link thật, dùng https://images.unsplash.com/photo-...?w=600
   - "fillInBlank": 1 đoạn tóm tắt 5–7 chỗ trống, dùng ___đáp_án___
     cho các từ nằm trong vocabulary.

4) "matchingPictures" (cả 2 layout): mảng {"word","pic"}.
   Chọn 4–6 từ CÓ THỂ vẽ bằng hình ảnh.
   pic = URL Unsplash khuyến nghị, hoặc placeholder:
   https://via.placeholder.com/300x200?text=Word

5) "matchingSynonyms" (cả 2 layout): mảng {"word","synonym"}.
   Mỗi từ có đúng 1 từ đồng nghĩa tiếng Anh.

6) "mcqQuestions": mảng {"q","options","answer"}.
   - options: đúng 4 lựa chọn.
   - answer: CHỈ SỐ (0-based) của đáp án đúng trong options.
     (phần tử đầu = 0, KHÔNG dùng 1-based)
   - Câu hỏi phải dựa trên nội dung bài test.

7) Các trường meta: "id","title","description","layout","duration",
   "level","tags" (mảng chữ thường).

================= QUY TẮC JSON BẮT BUỘC =================
- CHỈ trả về 1 khối JSON hợp lệ, không markdown thừa, không comment.
- Ngoặc kép ", escape " bên trong chuỗi bằng \".
- Xuống dòng trong chuỗi dùng \n (KHÔNG xuống dòng thật).
- KHÔNG trailing comma.

================= VÍ DỤ CẤU TRÚC (tham khảo) =================
{
 "id":"listening-1","title":"...","layout":"listening",
 "youtubeVideo":"","duration":"15 min","level":"B1","tags":["b1"],
 "transcript":"... you have ___nailed___ it ...",
 "vocabulary":[{"word":"Nailed it","ipa":"/neɪld ɪt/","wordForm":"Idiom",
   "meaning":"Làm xuất sắc","example":"You have nailed it!"}],
 "matchingPictures":[{"word":"Skill","pic":"https://..."}],
 "matchingSynonyms":[{"word":"Skill","synonym":"Ability"}],
 "mcqQuestions":[{"q":"...","options":["A","B","C","D"],"answer":1}]
}

Bây giờ hãy tạo file JSON hoàn chỉnh cho THÔNG SỐ + NỘI DUNG trên.
