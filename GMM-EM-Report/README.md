# GMM-EM Report – Hướng dẫn cho nhóm

Báo cáo về **Mô hình Hỗn hợp Gaussian (GMM) và Thuật toán EM** viết bằng LaTeX.

---

## Cấu trúc thư mục

```
GMM-EM-Report/
├── main.tex                    ← File gốc, KHÔNG chỉnh sửa
├── preamble.tex                ← Cấu hình gói, macro — KHÔNG chỉnh sửa
├── references.bib              ← Thêm tài liệu tham khảo vào đây
├── chapters/
│   ├── 01_introduction.tex          ← Thành viên: [Tên]
│   ├── 02_mathematical_foundations.tex  ← Thành viên: [Tên]
│   ├── 03_gaussian_mixture_model.tex    ← Thành viên: [Tên]
│   ├── 04_expectation_maximization.tex  ← Thành viên: [Tên] ✅ ĐÃ VIẾT
│   ├── 05_kmeans_vs_gmm.tex         ← Thành viên: [Tên]
│   ├── 06_experiments_results.tex   ← Thành viên: [Tên]
│   └── 07_conclusion.tex            ← Thành viên: [Tên]
├── figures/                    ← Lưu hình ảnh (.pdf, .png, .jpg)
├── tables/                     ← Lưu file bảng riêng nếu cần
└── code/                       ← Lưu code Python/notebook minh họa
```

---

## Quy tắc viết (bắt buộc)

### 1. Mỗi thành viên chỉ viết trong file chương được phân công
- **Không** chỉnh sửa `main.tex` hay `preamble.tex`
- Nếu cần thêm gói LaTeX → báo người quản lý để thêm vào `preamble.tex`

### 2. Ký hiệu toán học thống nhất — dùng macro đã định nghĩa

| Ký hiệu | Macro | Kết quả |
|---------|-------|---------|
| Vector dữ liệu | `\vx` | **x** |
| Vector trung bình | `\vmu` | **μ** |
| Ma trận hiệp phương sai | `\vSigma` | **Σ** |
| Phân phối Gaussian | `\Normal` | 𝒩 |
| Kỳ vọng | `\Exp` | 𝔼 |
| Responsibility | `\responsibility` | γ |
| argmax | `\argmax` | arg max |
| argmin | `\argmin` | arg min |
| Trace | `\tr` | tr |

**Ví dụ đúng:**
```latex
\Normal(\vx \mid \vmu_k, \vSigma_k)
\Exp_{Z \mid X, \vtheta^{(t)}}[\log p(X,Z \mid \vtheta)]
```

### 3. Chèn hình ảnh
- Lưu file hình vào thư mục `figures/`
- Dùng mẫu sau:

```latex
\begin{figure}[H]
  \centering
  \includegraphics[width=0.8\linewidth]{figures/ten_hinh.pdf}
  \caption{Mô tả hình}
  \label{fig:ten_label}
\end{figure}
```

### 4. Chèn bảng
- Dùng `\toprule`, `\midrule`, `\bottomrule` (từ gói `booktabs`)
- Tham khảo bảng mẫu trong `chapters/05_kmeans_vs_gmm.tex`

### 5. Trích dẫn tài liệu
- Thêm entry vào `references.bib` rồi dùng `\cite{key}` trong văn bản
- Ví dụ: `\cite{bishop2006prml}`, `\cite{dempster1977em}`

### 6. Đánh dấu công việc còn dang dở
Dùng comment `% TODO:` để đánh dấu phần chưa hoàn thiện:
```latex
% TODO: Viết phân tích hội tụ
```

---

## Cách biên dịch

### Yêu cầu
- **TeX distribution:** TeX Live 2022+ hoặc MiKTeX
- **Engine:** `pdflatex` hoặc `xelatex`
- **Bibliography:** `biber` (đã cấu hình trong `preamble.tex`)

### Biên dịch thủ công (terminal)
```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```

### Dùng VS Code + LaTeX Workshop
1. Cài extension **LaTeX Workshop**
2. Mở `main.tex` → nhấn `Ctrl+Alt+B` để build
3. Xem PDF bằng `Ctrl+Alt+V`

### Dùng Overleaf
1. Zip toàn bộ thư mục → upload lên [overleaf.com](https://overleaf.com)
2. Đặt compiler thành **pdfLaTeX**, bibliography tool thành **Biber**

---

## Phân công thành viên

| Chương | Nội dung | Thành viên | Deadline |
|--------|----------|-----------|---------|
| 1 | Giới thiệu | [Tên] | |
| 2 | Nền tảng toán học | [Tên] | |
| 3 | Mô hình GMM | [Tên] | |
| 4 | E-step & M-step | [Tên] | ✅ |
| 5 | So sánh GMM vs k-means | [Tên] | |
| 6 | Thực nghiệm | [Tên] | |
| 7 | Kết luận | [Tên] | |

---

## Macro hữu ích trong preamble

```latex
% Hộp công thức nổi bật (màu xanh)
\begin{formulabox}[Tiêu đề hộp]
  Nội dung công thức ...
\end{formulabox}

% Hộp lưu ý (màu cam)
\begin{notebox}[Lưu ý]
  Nội dung cảnh báo ...
\end{notebox}
```
