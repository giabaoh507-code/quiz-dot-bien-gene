<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ngân Hàng Lý Thuyết Đột Biến Gene - Trọn Bộ</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-slate-100 text-slate-800 min-h-screen py-8 px-4 font-sans">
  <div class="max-w-4xl mx-auto space-y-6">

    <!-- HEADER -->
    <header class="text-center bg-white p-6 rounded-2xl shadow-sm border border-slate-200">
      <div class="inline-block bg-indigo-100 text-indigo-800 text-xs px-3 py-1 rounded-full font-bold uppercase tracking-wider mb-2">Sinh Học 12 - Ôn Thi THPTQG</div>
      <h1 class="text-2xl md:text-3xl font-extrabold text-slate-900">CHUYÊN ĐỀ LÝ THUYẾT: ĐỘT BIẾN GENE (TRỌN BỘ)</h1>
      <p class="text-slate-500 text-sm mt-1">Trọn vẹn 32 câu TLN • Toàn bộ TN lý thuyết tài liệu • Toàn bộ ĐS chùm 4 ý</p>
    </header>

    <!-- BỘ LỌC VÀ ĐIỀU HƯỚNG -->
    <div class="bg-white p-4 rounded-xl shadow-sm border border-slate-200 flex flex-wrap items-center justify-between gap-4">
      <div class="flex items-center gap-2">
        <label class="font-bold text-sm text-slate-700">Chế độ luyện tập:</label>
        <select id="filterType" onchange="renderQuiz()" class="border border-slate-300 rounded-lg p-2 bg-slate-50 text-sm font-semibold outline-indigo-500 text-indigo-900">
          <option value="ALL">Toàn bộ ngân hàng câu hỏi</option>
          <option value="TLN">32 Câu Tự Luận Ngắn (TLN)</option>
          <option value="TN">Trắc Nghiệm 4 Phương Án (TN)</option>
          <option value="DS">Đúng / Sai Cụm 4 Ý (ĐS)</option>
        </select>
      </div>

      <div class="flex items-center gap-3">
        <button onclick="shuffleQuestions()" class="text-xs md:text-sm bg-indigo-50 hover:bg-indigo-100 text-indigo-700 font-bold py-2 px-3.5 rounded-lg transition border border-indigo-200">
          🔀 Đảo ngẫu nhiên
        </button>
        <span id="statBadge" class="text-xs bg-slate-100 text-slate-600 px-3 py-2 rounded-lg font-bold">0 câu</span>
      </div>
    </div>

    <!-- KHU VỰC CÂU HỎI -->
    <div id="quizContainer" class="space-y-6"></div>

    <!-- NÚT NỘP BÀI CỐ ĐỊNH -->
    <div class="sticky bottom-4 bg-white/95 backdrop-blur p-4 rounded-2xl shadow-xl border border-slate-200 flex flex-col md:flex-row gap-4 items-center justify-between z-20">
      <div id="scoreDisplay" class="font-bold text-slate-800 text-base">Hoàn thành bài làm rồi nhấn "Nộp bài & Chấm điểm".</div>
      <div class="flex gap-3 w-full md:w-auto">
        <button onclick="gradeAll()" class="flex-1 md:flex-initial bg-emerald-600 hover:bg-emerald-700 text-white font-bold py-2.5 px-6 rounded-xl transition shadow">
          Nộp bài & Chấm điểm
        </button>
        <button onclick="renderQuiz()" class="bg-slate-200 hover:bg-slate-300 text-slate-700 font-semibold py-2.5 px-4 rounded-xl transition">
          Làm lại từ đầu
        </button>
      </div>
    </div>

  </div>

  <script>
    const questionBank = [
      /* =========================================================================
         PHẦN 1: ĐẦY ĐỦ 32 CÂU TỰ LUẬN NGẮN (TLN)
      ========================================================================= */
      {
        id: "TLN_01",
        type: "TLN",
        title: "C1 (TLN). Đột biến gene là những thay đổi của gì?",
        answers: ["gene liên quan đến một hay một số cặp nucleotide", "một hay một số cặp nucleotide", "cấu trúc của gene liên quan đến một hay một số cặp nucleotide", "cấu trúc của gene"],
        hint: "Liên quan đến đơn phân nucleotide của gene",
        explanation: "Đột biến gene là những thay đổi trong cấu trúc của gene, liên quan đến một hay một số cặp nucleotide."
      },
      {
        id: "TLN_02",
        type: "TLN",
        title: "C2 (TLN). Đột biến liên quan đến một số cặp nucleotide được gọi là gì? (Hoặc biến đổi ở 1 cặp nu)",
        answers: ["đột biến điểm", "dot bien diem"],
        hint: "Xảy ra tại một điểm",
        explanation: "Đột biến liên quan đến một cặp nucleotide được gọi là đột biến điểm."
      },
      {
        id: "TLN_03",
        type: "TLN",
        title: "C3 (TLN). Đột biến gene làm xuất hiện gì?",
        answers: ["các allele mới", "các alen mới", "allele mới", "alen mới"],
        hint: "Các trạng thái khác nhau của cùng 1 gene",
        explanation: "Đột biến gene làm xuất hiện các allele mới, làm phong phú vốn gene của quần thể."
      },
      {
        id: "TLN_04",
        type: "TLN",
        title: "C4 (TLN). Tần số đột biến gene phụ thuộc vào những yếu tố nào?",
        answers: ["điều kiện môi trường, cấu trúc và kích thước của gene", "môi trường, cấu trúc và kích thước của gene", "điều kiện môi trường và cấu trúc của gene"],
        hint: "Tác nhân bên ngoài và đặc điểm bên trong của gene",
        explanation: "Tần số đột biến phụ thuộc vào điều kiện môi trường, cấu trúc và kích thước của gene."
      },
      {
        id: "TLN_05",
        type: "TLN",
        title: "C5 (TLN). Tần số đột biến 1 gene bất kì trong tự nhiên khoảng bao nhiêu?",
        answers: ["10^-6 – 10^-4", "10^-6 đến 10^-4", "10-6 đến 10-4", "10-6 - 10-4"],
        hint: "Từ một phần triệu đến một phần vạn",
        explanation: "Tần số đột biến tự nhiên của một gene bất kì thường rất thấp, dao động từ 10^-6 đến 10^-4."
      },
      {
        id: "TLN_06",
        type: "TLN",
        title: "C6 (TLN). Có những dạng đột biến gene (đột biến điểm) cơ bản nào?",
        answers: ["thêm một cặp nu, mất một cặp nu và thay thế một cặp nu", "thêm, mất, thay thế", "thay thế một cặp nu, thêm một cặp nu, mất một cặp nu", "thêm một cặp nu, mất một cặp nu, thay thế một cặp nu"],
        hint: "Gồm 3 dạng cơ bản: Thêm, Mất và...",
        explanation: "Các dạng đột biến điểm cơ bản: Thêm một cặp nu, mất một cặp nu và thay thế một cặp nu."
      },
      {
        id: "TLN_07",
        type: "TLN",
        title: "C7 (TLN). Đột biến thay thế một cặp nucleotide có thể làm thay đổi gì?",
        answers: ["trình tự amino acid trong chuỗi polypeptide và chức năng của protein", "trình tự amino acid và chức năng protein", "trình tự amino acid"],
        hint: "Ảnh hưởng tới cấu trúc chuỗi polypeptide và hoạt tính protein",
        explanation: "Có thể làm thay đổi trình tự amino acid trong chuỗi polypeptide và chức năng của protein."
      },
      {
        id: "TLN_08",
        type: "TLN",
        title: "C8 (TLN). Đột biến thay thế nhưng không thay đổi trình tự amino acid là đột biến gì?",
        answers: ["đồng nghĩa", "đột biến đồng nghĩa", "dong nghia"],
        hint: "Mã hóa cùng một loại amino acid (tính thoái hóa)",
        explanation: "Đột biến đồng nghĩa (silent mutation): thay thế nu nhưng codon mới vẫn mã hóa cho amino acid đó."
      },
      {
        id: "TLN_09",
        type: "TLN",
        title: "C9 (TLN). Đột biến tạo ra bộ ba kết thúc sớm là đột biến gì?",
        answers: ["vô nghĩa", "đột biến vô nghĩa", "vo nghia"],
        hint: "Làm chuỗi polypeptide bị ngắn lại",
        explanation: "Đột biến vô nghĩa (nonsense mutation): biến một bộ ba mã hóa thành bộ ba kết thúc dịch mã sớm."
      },
      {
        id: "TLN_10",
        type: "TLN",
        title: "C10 (TLN). Đột biến làm thay đổi 1 amino acid này bằng 1 amino acid khác là đột biến gì?",
        answers: ["sai nghĩa", "đột biến sai nghĩa", "sai nghia"],
        hint: "Thay đổi nghĩa của codon",
        explanation: "Đột biến sai nghĩa (missense mutation): codon bị biến đổi mã hóa cho một amino acid khác."
      },
      {
        id: "TLN_11",
        type: "TLN",
        title: "C11 (TLN). Thêm hoặc mất một cặp nu còn gọi là đột biến gì?",
        answers: ["dịch khung", "đột biến dịch khung", "dich khung"],
        hint: "Lệch khung đọc mã di truyền",
        explanation: "Đột biến thêm hoặc mất 1 cặp nu làm lệch khung đọc kể từ điểm đột biến nên gọi là đột biến dịch khung."
      },
      {
        id: "TLN_12",
        type: "TLN",
        title: "C12 (TLN). Đột biến dịch khung làm thay đổi gì?",
        answers: ["trình tự amino acid kể từ một vị trí trở về sau", "trình tự amino acid từ vị trí đột biến đến cuối chuỗi", "trình tự amino acid kể từ vị trí đột biến"],
        hint: "Ảnh hưởng từ điểm đột biến về sau",
        explanation: "Làm thay đổi trình tự amino acid kể từ vị trí xảy ra đột biến trở về sau."
      },
      {
        id: "TLN_13",
        type: "TLN",
        title: "C13 (TLN). Nguyên nhân tự phát của đột biến gene là gì?",
        answers: ["hiện tượng cặp nhầm trong tái bản dna", "cặp nhầm trong tái bản dna", "nhân đôi dna cặp nhầm", "bắt cặp nhầm trong nhân đôi dna"],
        hint: "Bắt cặp sai nguyên tắc trong nhân đôi",
        explanation: "Nguyên nhân tự phát là do hiện tượng bắt cặp nhầm không theo NTBS trong quá trình tái bản DNA."
      },
      {
        id: "TLN_14",
        type: "TLN",
        title: "C14 (TLN). Có mấy nhóm tác nhân đột biến?",
        answers: ["3 nhóm: vật lí, hóa học, sinh học", "vật lí, hóa học, sinh học", "3", "3 nhóm"],
        hint: "Bao gồm môi trường bức xạ, hóa chất và sinh vật",
        explanation: "Có 3 nhóm tác nhân chính: Vật lí, hóa học và sinh học."
      },
      {
        id: "TLN_15",
        type: "TLN",
        title: "C15 (TLN). Tia phóng xạ, tia tử ngoại, tia UV, nhiệt thuộc tác nhân nào?",
        answers: ["vật lí", "vat li", "tác nhân vật lí"],
        hint: "Bức xạ và năng lượng",
        explanation: "Thuộc nhóm tác nhân vật lí."
      },
      {
        id: "TLN_16",
        type: "TLN",
        title: "C16 (TLN). Các chất EMS, NMV thuộc tác nhân nào?",
        answers: ["hóa học", "hoa hoc", "tác nhân hóa học"],
        hint: "Các hóa chất gây đột biến",
        explanation: "Thuộc nhóm tác nhân hóa học."
      },
      {
        id: "TLN_17",
        type: "TLN",
        title: "C17 (TLN). Virus viêm gan B, HPV thuộc tác nhân nào?",
        answers: ["sinh học", "sinh hoc", "tác nhân sinh học"],
        hint: "Các tác nhân vi sinh vật sống",
        explanation: "Thuộc nhóm tác nhân sinh học."
      },
      {
        id: "TLN_18",
        type: "TLN",
        title: "C18 (TLN). Cơ chế dẫn đến đột biến thêm cặp nucleotide là gì?",
        answers: ["một nucleotide được sử dụng làm khuôn 2 lần", "1 nu được làm khuôn 2 lần", "nucleotide làm khuôn 2 lần"],
        hint: "Một nucleotide khuôn được đọc lặp lại",
        explanation: "Cơ chế: Một nucleotide trên mạch khuôn được sử dụng làm khuôn 2 lần."
      },
      {
        id: "TLN_19",
        type: "TLN",
        title: "C19 (TLN). Kết quả của việc một nucleotide được sử dụng làm khuôn 2 lần?",
        answers: ["mạch mới tổng hợp sẽ có thêm một nucleotide", "mạch mới có thêm một nucleotide", "thêm một nucleotide ở mạch mới"],
        hint: "Mạch mới được bổ sung thêm gì?",
        explanation: "Mạch mới tổng hợp sẽ có thêm một nucleotide."
      },
      {
        id: "TLN_20",
        type: "TLN",
        title: "C20 (TLN). Cơ chế dẫn đến đột biến mất cặp nucleotide?",
        answers: ["1 nu không được làm khuôn", "một nucleotide không được sử dụng làm khuôn", "1 nu bị bỏ qua không làm khuôn"],
        hint: "Ngược lại với cơ chế thêm nu",
        explanation: "Cơ chế: Một nucleotide trên mạch khuôn không được sử dụng làm khuôn (bị trượt qua)."
      },
      {
        id: "TLN_21",
        type: "TLN",
        title: "C21 (TLN). Khi 1 nu không được làm khuôn thì điều gì xảy ra?",
        answers: ["mạch mới tổng hợp bị mất một nu", "mạch mới mất một nucleotide", "mất một nu ở mạch mới"],
        hint: "Mạch mới bị thiếu hụt gì?",
        explanation: "Mạch mới tổng hợp bị mất một nucleotide."
      },
      {
        id: "TLN_22",
        type: "TLN",
        title: "C22 (TLN). Cơ chế gây đột biến thay thế cặp nucleotide là gì?",
        answers: ["một số chất có cấu trúc giống base bình thường được gắn vào mạch mới", "chất có cấu trúc giống base được gắn vào", "base tương đồng gắn vào mạch mới"],
        hint: "Do gắn nhầm chất có cấu trúc tương tự base",
        explanation: "Một số chất có cấu trúc giống base bình thường (hoặc base dạng hiếm) được gắn vào mạch mới."
      },
      {
        id: "TLN_23",
        type: "TLN",
        title: "C23 (TLN). Đa số đột biến gene có đặc điểm như thế nào?",
        answers: ["có hại", "co hai"],
        hint: "Thường phá vỡ sự hài hòa vốn có",
        explanation: "Đa số đột biến có hại cho cơ thể sinh vật."
      },
      {
        id: "TLN_24",
        type: "TLN",
        title: "C24 (TLN). Ngoài đột biến có hại còn có những loại nào?",
        answers: ["có lợi và trung tính", "trung tính và có lợi", "có lợi hoặc trung tính"],
        hint: "Không gây hại hoặc mang lại ưu thế",
        explanation: "Ngoài có hại, đột biến gene còn có thể có lợi và trung tính."
      },
      {
        id: "TLN_25",
        type: "TLN",
        title: "C25 (TLN). Đột biến gene được sử dụng trong nghiên cứu di truyền để xác định gì?",
        answers: ["gene trội/lặn, các quy luật di truyền, dự đoán sự biểu hiện tính trạng tương ứng ở thế hệ tiếp theo", "gene trội lặn và các quy luật di truyền", "gene trội lặn"],
        hint: "Mối quan hệ alen và quy luật phân ly/liên kết",
        explanation: "Xác định gene trội/lặn, các quy luật di truyền, dự đoán sự biểu hiện tính trạng tương ứng ở thế hệ tiếp theo."
      },
      {
        id: "TLN_26",
        type: "TLN",
        title: "C26 (TLN). Đột biến gene được sử dụng để làm gì trong nghiên cứu mã di truyền?",
        answers: ["xây dựng bảng mã di truyền", "xay dung bang ma di truyen", "bảng mã di truyền"],
        hint: "Bảng 64 bộ ba codon",
        explanation: "Đột biến gene được sử dụng để xây dựng bảng mã di truyền."
      },
      {
        id: "TLN_27",
        type: "TLN",
        title: "C27 (TLN). Đột biến gene giúp nghiên cứu gì?",
        answers: ["chức năng gene", "chức năng của gene", "chuc nang gene"],
        hint: "Nhiệm vụ sinh học của gene đó",
        explanation: "Đột biến gene giúp nghiên cứu chức năng của gene."
      },
      {
        id: "TLN_28",
        type: "TLN",
        title: "C28 (TLN). Đột biến gene giúp làm sáng tỏ mối quan hệ nào?",
        answers: ["mối quan hệ giữa gene và protein", "gene và protein", "quan hệ giữa gene và protein"],
        hint: "Giữa DNA mang mã và sản phẩm hoạt tính",
        explanation: "Đột biến gene giúp làm sáng tỏ mối quan hệ giữa gene và protein."
      },
      {
        id: "TLN_29",
        type: "TLN",
        title: "C29 (TLN). Dựa vào thể đột biến có thể làm gì?",
        answers: ["phát hiện các đột biến có lợi hoặc có hại", "phát hiện đột biến có lợi và có hại", "sàng lọc đột biến có lợi hoặc có hại"],
        hint: "Sàng lọc và phân loại giá trị đột biến",
        explanation: "Dựa vào thể đột biến có thể phát hiện các đột biến có lợi hoặc có hại."
      },
      {
        id: "TLN_30",
        type: "TLN",
        title: "C30 (TLN). Trong chọn giống, đột biến gene có vai trò gì?",
        answers: ["tạo ra giống mới", "tạo giống mới", "cung cấp nguyên liệu tạo giống mới"],
        hint: "Hình thành các giống sinh vật mới",
        explanation: "Trong chọn giống, đột biến gene có vai trò tạo ra giống mới."
      },
      {
        id: "TLN_31",
        type: "TLN",
        title: "C31 (TLN). Trong tiến hóa, đột biến cung cấp gì?",
        answers: ["nguồn nguyên liệu cho quá trình tiến hóa", "nguyên liệu sơ cấp", "nguyên liệu cho tiến hóa", "nguồn nguyên liệu sơ cấp"],
        hint: "Nguyên liệu sơ cấp đầu tiên",
        explanation: "Trong tiến hóa, đột biến cung cấp nguồn nguyên liệu cho quá trình tiến hóa."
      },
      {
        id: "TLN_32",
        type: "TLN",
        title: "C32 (TLN). Đột biến giúp giải thích điều gì?",
        answers: ["tính đa dạng của sinh giới, cơ chế góp phần hình thành loài mới", "tính đa dạng của sinh giới và hình thành loài mới", "tính đa dạng của sinh giới"],
        hint: "Sự phong phú về loài và nguồn gốc loài mới",
        explanation: "Đột biến giúp giải thích tính đa dạng của sinh giới, cơ chế góp phần hình thành loài mới."
      },

      /* =========================================================================
         PHẦN 2: TOÀN BỘ TRẮC NGHIỆM LÝ THUYẾT (TN) TỪ TÀI LIỆU
      ========================================================================= */
      {
        id: "TN_01",
        type: "TN",
        title: "Câu 1 (TN). Đột biến gene là những biến đổi:",
        options: [
          "A. vật chất di truyền ở cấp độ phân tử hoặc cấp độ tế bào.",
          "B. trong cấu trúc của gene, liên quan đến một hoặc một số nucleotide tại một điểm nào đó trên DNA.",
          "C. trong cấu trúc của gene, liên quan đến một hoặc một số cặp nucleotide tại một điểm nào đó trên DNA.",
          "D. trong cấu trúc của nhiễm sắc thể, xảy ra trong quá trình phân chia tế bào."
        ],
        correctAnswer: 2,
        explanation: "Đột biến gene là những biến đổi trong cấu trúc của gene, liên quan tới một hoặc một số cặp nucleotide."
      },
      {
        id: "TN_02",
        type: "TN",
        title: "Câu 2 (TN). Trong đột biến gene thì đột biến điểm là loại đột biến liên quan đến biến đổi mấy cặp nucleotide?",
        options: [
          "A. Một số cặp nucleotide.",
          "B. Hai cặp nucleotide.",
          "C. Ba cặp nucleotide.",
          "D. Một cặp nucleotide."
        ],
        correctAnswer: 3,
        explanation: "Đột biến điểm chỉ liên quan đến biến đổi của đúng 1 cặp nucleotide."
      },
      {
        id: "TN_05",
        type: "TN",
        title: "Câu 5 (TN). Đột biến điểm làm thay thế 1 nucleotide ở vị trí bất kì của triplet nào sau đây đều không xuất hiện codon kết thúc?",
        options: [
          "A. 3’AXX5'.",
          "B. 3’AXA5'.",
          "C. 3’AAT5’.",
          "D. 3’AGG5'."
        ],
        correctAnswer: 3,
        explanation: "Bộ ba kết thúc gồm: 5'UAA3', 5'UAG3', 5'UGA3' ứng với triplet khuôn 3'ATT5', 3'ATC5', 3'ACT5'. Triplet 3'AGG5' có 2 nu G nên thay thế 1 nu bất kỳ không thể tạo ra triplet kết thúc."
      },
      {
        id: "TN_06",
        type: "TN",
        title: "Câu 6 (TN). Trong đột biến gene thì đột biến điểm là loại đột biến liên quan đến biến đổi …(1)… cặp nucleotide.",
        options: [
          "A. 1 – một.",
          "B. 1 – hai.",
          "C. 1 – ba.",
          "D. 1 – một số."
        ],
        correctAnswer: 0,
        explanation: "Đột biến điểm là biến đổi liên quan đến đúng 1 cặp nucleotide."
      },
      {
        id: "TN_07",
        type: "TN",
        title: "Câu 7 (TN). Base nitrogenous dạng hiếm Thymine (T*) sẽ tạo nên đột biến điểm dạng nào sau đây?",
        options: [
          "A. Mất một cặp A – T.",
          "B. Thêm một cặp G – C.",
          "C. Thay thế cặp G – C bằng cặp A – T.",
          "D. Thay thế A – T bằng cặp G – C."
        ],
        correctAnswer: 3,
        explanation: "T* kết cặp với G qua nhân đôi dẫn đến thay thế cặp A-T bằng G-C."
      },
      {
        id: "TN_08",
        type: "TN",
        title: "Câu 8 (TN). Tác nhân gây đột biến base dạng hiếm thuộc nhóm nguyên nhân nào?",
        options: [
          "A. Tự rối loạn sinh lý nội bào.",
          "B. Tác nhân vật lí.",
          "C. Tác nhân hóa học.",
          "D. Tác nhân sinh học."
        ],
        correctAnswer: 0,
        explanation: "Sự xuất hiện bazơ nitơ dạng hiếm là hiện tượng hỗ biến tự nhiên trong tế bào (tự rối loạn)."
      },
      {
        id: "TN_09",
        type: "TN",
        title: "Câu 9 (TN). Tác nhân nào làm cho 2 base Timin trên một mạch của DNA liên kết lại với nhau?",
        options: [
          "A. Tia UV.",
          "B. 5-BU.",
          "C. Base nitrogenous dạng hiếm.",
          "D. Virus."
        ],
        correctAnswer: 0,
        explanation: "Tia UV kích thích làm hình thành dimer thymine giữa 2 bazơ T kề nhau trên cùng một mạch."
      },
      {
        id: "TN_10",
        type: "TN",
        title: "Câu 10 (TN). Tác nhân gây đột biến 5 – BU thuộc nhóm nguyên nhân nào?",
        options: [
          "A. Tự rối loạn.",
          "B. Tác nhân vật lí.",
          "C. Tác nhân hóa học.",
          "D. Tác nhân sinh học."
        ],
        correctAnswer: 2,
        explanation: "5-BU là chất hóa học đồng đẳng với Timin."
      },
      {
        id: "TN_11",
        type: "TN",
        title: "Câu 11 (TN). Tác nhân gây đột biến tia UV thuộc nhóm nguyên nhân nào?",
        options: [
          "A. Tự rối loạn.",
          "B. Tác nhân vật lí.",
          "C. Tác nhân hóa học.",
          "D. Tác nhân sinh học."
        ],
        correctAnswer: 1,
        explanation: "Tia tử ngoại (UV) là bức xạ điện từ, thuộc tác nhân vật lí."
      },
      {
        id: "TN_13",
        type: "TN",
        title: "Câu 13 (TN). Tác nhân gây đột biến một số virus thuộc nhóm nguyên nhân nào?",
        options: [
          "A. Tự rối loạn.",
          "B. Tác nhân vật lí.",
          "C. Tác nhân hóa học.",
          "D. Tác nhân sinh học."
        ],
        correctAnswer: 3,
        explanation: "Virus là tác nhân sinh học."
      },
      {
        id: "TN_14",
        type: "TN",
        title: "Câu 14 (TN). Quá trình nào thường dễ làm phát sinh đột biến gene nhất?",
        options: [
          "A. Phiên mã và dịch mã.",
          "B. Dịch mã.",
          "C. Phiên mã.",
          "D. Nhân đôi DNA."
        ],
        correctAnswer: 3,
        explanation: "Quá trình nhân đôi DNA tháo xoắn và bắt cặp các nu tự do nên dễ phát sinh cặp nhầm."
      },
      {
        id: "TN_17",
        type: "TN",
        title: "Câu 17 (TN). Loại đột biến nào làm tăng số loại allele của một gene nào đó trong vốn gene của quần thể?",
        options: [
          "A. Tự đa bội.",
          "B. Chuyển đoạn.",
          "C. Lặp đoạn.",
          "D. Đột biến điểm."
        ],
        correctAnswer: 3,
        explanation: "Đột biến điểm làm biến đổi cấu trúc gene, sinh ra các allele mới trong quần thể."
      },
      {
        id: "TN_21",
        type: "TN",
        title: "Câu 21 (TN). Đột biến gene có ba dạng cơ bản là:",
        options: [
          "A. Đảo một cặp nucleotide, thay thế một cặp nucleotide và vận chuyển một cặp nucleotide.",
          "B. Thay thế một cặp nucleotide, thêm một cặp nucleotide và mất một cặp nucleotide.",
          "C. Mất một cặp nucleotide, thêm một cặp nucleotide và đảo vị trí hai cặp nucleotide.",
          "D. Thay thế một cặp nucleotide, chuyển một cặp nucleotide và thêm một cặp nucleotide."
        ],
        correctAnswer: 1,
        explanation: "3 dạng đột biến điểm cơ bản: Thay thế, thêm và mất 1 cặp nucleotide."
      },
      {
        id: "TN_22",
        type: "TN",
        title: "Câu 22 (TN). Điều KHÔNG đúng về đột biến gene là:",
        options: [
          "A. Làm biến đổi toàn bộ cấu trúc của gene.",
          "B. Có thể có lợi, có hại hoặc trung tính.",
          "C. Có thể làm cho sinh vật ngày càng đa dạng, phong phú.",
          "D. Làm nguyên liệu của quá trình chọn giống và tiến hoá."
        ],
        correctAnswer: 0,
        explanation: "A sai vì đột biến gene chỉ làm biến đổi tại 1 hoặc 1 số cặp nu, không biến đổi toàn bộ gene."
      },
      {
        id: "TN_24",
        type: "TN",
        title: "Câu 24 (TN). Trong vùng mã hóa của mRNA, đột biến làm xuất hiện codon nào sau đây sẽ kết thúc sớm dịch mã?",
        options: [
          "A. 5'UAG3'.",
          "B. 5’UUA3'.",
          "C. 5’UGG3’.",
          "D. 3’UAA5'."
        ],
        correctAnswer: 0,
        explanation: "Codon 5'UAG3' là một trong 3 codon kết thúc chuẩn."
      },
      {
        id: "TN_25",
        type: "TN",
        title: "Câu 25 (TN). Trong số các dạng đột biến sau đây dạng nào thường gây hậu quả ít nhất?",
        options: [
          "A. Đột biến mất đoạn NST.",
          "B. Mất 1 cặp nucleotide.",
          "C. Thay thế một cặp nucleotide.",
          "D. Thêm một cặp nucleotide."
        ],
        correctAnswer: 2,
        explanation: "Thay thế 1 cặp nu chỉ ảnh hưởng tối đa 1 amino acid (hoặc không đổi do tính thoái hóa)."
      },
      {
        id: "TN_27",
        type: "TN",
        title: "Câu 27 (TN). Đối với từng gene riêng rẽ thì tần số đột biến tự nhiên trung bình là:",
        options: [
          "A. 10^-1.",
          "B. 10^-6 đến 10^-4.",
          "C. 10^-2 đến 10^-1.",
          "D. 10^-4."
        ],
        correctAnswer: 1,
        explanation: "Tần số đột biến tự nhiên trung bình ở mỗi gene là 10^-6 đến 10^-4."
      },
      {
        id: "TN_29",
        type: "TN",
        title: "Câu 29 (TN). Một bazơ nitơ của gene trở thành dạng hiếm thì qua quá trình nhân đôi của DNA sẽ làm phát sinh dạng đột biến:",
        options: [
          "A. Thêm 2 cặp nucleotide.",
          "B. Thêm 1 cặp nucleotide.",
          "C. Mất một cặp nucleotide.",
          "D. Thay thế 1 cặp nucleotide."
        ],
        correctAnswer: 3,
        explanation: "Bazơ nitơ dạng hiếm làm phát sinh đột biến thay thế 1 cặp nucleotide."
      },
      {
        id: "TN_31",
        type: "TN",
        title: "Câu 31 (TN). Loại đột biến khi xảy ra có thể không làm thay đổi số lượng amino acid và trình tự các amino acid trong polypeptide thuộc dạng:",
        options: [
          "A. Không có dạng đột biến nào.",
          "B. Thêm một cặp nucleotide ở ngay sau bộ ba mở đầu.",
          "C. Mất một cặp nucleotide ở gần bộ ba kết thúc.",
          "D. Thay thế nucleotide cùng trong các bộ ba mã hoá amino acid."
        ],
        correctAnswer: 3,
        explanation: "Đột biến thay thế cùng mã hóa 1 amino acid (đột biến đồng nghĩa) giữ nguyên trình tự và số lượng amino acid."
      },
      {
        id: "TN_37",
        type: "TN",
        title: "Câu 37 (TN). Phát biểu nào sau đây về đột biến gene là SAI?",
        options: [
          "A. Đột biến gene làm xuất hiện các allele khác nhau cung cấp nguyên liệu cho quá trình tiến hoá.",
          "B. Đột biến thay thế một cặp nucleotide luôn làm thay đổi chức năng của protein.",
          "C. Mức độ gây hại của allele đột biến phụ thuộc vào điều kiện môi trường và tổ hợp gene.",
          "D. Đột biến gene có thể có hại, có lợi hoặc trung tính đối với thể đột biến."
        ],
        correctAnswer: 1,
        explanation: "B sai vì có thể là đột biến đồng nghĩa hoặc không làm thay đổi chức năng protein."
      },
      {
        id: "TN_38",
        type: "TN",
        title: "Câu 38 (TN). Loại đột biến nào sau đây được gọi là nguyên liệu sơ cấp của quá trình tiến hóa?",
        options: [
          "A. Đột biến gene.",
          "B. Đột biến đa bội.",
          "C. Đột biến lệch bội dạng thể ba.",
          "D. Đột biến lặp đoạn NST."
        ],
        correctAnswer: 0,
        explanation: "Đột biến gene cung cấp các allele mới, là nguyên liệu sơ cấp của tiến hóa."
      },
      {
        id: "TN_41",
        type: "TN",
        title: "Câu 41 (TN). Sơ đồ nào mô tả đúng cơ chế gây đột biến làm thay thế cặp A-T bằng cặp G-C của bazơnitơ dạng hiếm?",
        options: [
          "A. A-T* → T*-G → G-C.",
          "B. A-T* → A-G → G-C.",
          "C. A-T* → G-T* → G-C.",
          "D. A-T* → T*-C → G-C."
        ],
        correctAnswer: 2,
        explanation: "T* dạng hiếm liên kết với G qua nhân đôi, sau đó G liên kết với C chuẩn tạo sơ đồ: A-T* -> G-T* -> G-C."
      },
      {
        id: "TN_44",
        type: "TN",
        title: "Câu 44 (TN). Dạng đột biến nào sau đây không làm thay đổi thành phần nucleotide của gene?",
        options: [
          "A. Thêm 1 cặp nucleotide.",
          "B. Mất 1 cặp nucleotide.",
          "C. Thay thế 1 cặp A - T bằng 1 cặp G - C.",
          "D. Thay thế 1 cặp A - T bằng 1 cặp T - A."
        ],
        correctAnswer: 3,
        explanation: "Thay thế A-T bằng T-A chỉ đảo vị trí trên 2 mạch chứ số lượng và thành phần nu của gene không đổi."
      },
      {
        id: "TN_45",
        type: "TN",
        title: "Câu 45 (TN). Khi nói về đột biến gene, phát biểu nào sau đây đúng?",
        options: [
          "A. Đột biến gene có thể làm thay đổi số lượng NST.",
          "B. Đột biến gene có thể làm phát sinh các allele mới, làm phong phú thêm vốn gene của quần thể.",
          "C. Đột biến thay thế 1 cặp nucleotide trong gene luôn làm thay đổi 1 acid amin của chuỗi polypeptide.",
          "D. Đột biến gene là những biến đổi trong cấu trúc của các phân tử acid nucleic."
        ],
        correctAnswer: 1,
        explanation: "B đúng. A sai vì không đổi số lượng NST; C sai do mã thoái hóa; D sai vì chỉ xét biến đổi cấu trúc DNA."
      },
      {
        id: "TN_46",
        type: "TN",
        title: "Câu 46 (TN). Khi nói về đột biến gene, phát biểu nào sau đây là đúng?",
        options: [
          "A. Đột biến gene luôn làm phát sinh các gene mới.",
          "B. Không có tác nhân đột biến vẫn có thể phát sinh đột biến gene.",
          "C. Đột biến gene là những biến đổi trong vùng mã hóa của gene.",
          "D. Đột biến nhân tạo có tần số thấp hơn các đột biến tự nhiên."
        ],
        correctAnswer: 1,
        explanation: "B đúng vì vẫn có thể phát sinh đột biến do tự rối loạn sinh lý nội bào (bắt cặp nhầm, bazơ hiếm)."
      },
      {
        id: "TN_47",
        type: "TN",
        title: "Câu 47 (TN). Timin dạng hiếm (T*) kết cặp với Guanin trong quá trình nhân đôi, tạo nên đột biến điểm dạng nào sau đây?",
        options: [
          "A. Mất một cặp A – T.",
          "B. Thêm một cặp G – C.",
          "C. Thay thế cặp G – C bằng cặp A – T.",
          "D. Thay thế A – T bằng cặp G – C."
        ],
        correctAnswer: 3,
        explanation: "T* làm thay thế cặp A-T thành G-C."
      },
      {
        id: "TN_48",
        type: "TN",
        title: "Câu 48 (TN). Trường hợp nào dưới đây KHÔNG phải là dạng đột biến điểm?",
        options: [
          "A. Mất đoạn NST.",
          "B. Thêm 1 cặp nucleotide.",
          "C. Thay thế 1 cặp nucleotide.",
          "D. Mất 1 cặp nucleotide."
        ],
        correctAnswer: 0,
        explanation: "Mất đoạn NST là đột biến cấu trúc nhiễm sắc thể, không phải đột biến điểm của gene."
      },
      {
        id: "TN_52",
        type: "TN",
        title: "Câu 52 (TN). Dạng đột biến nào sau đây là đột biến điểm?",
        options: [
          "A. Đảo đoạn NST.",
          "B. Mất 2 cặp nucleotide.",
          "C. Thêm 1 cặp nucleotide.",
          "D. Lặp đoạn NST."
        ],
        correctAnswer: 2,
        explanation: "Đột biến điểm liên quan đến đúng 1 cặp nu (Thêm 1 cặp nu)."
      },
      {
        id: "TN_55",
        type: "TN",
        title: "Câu 55 (TN). Theo thuyết tiến hóa tổng hợp hiện đại, nhân tố cung cấp nguyên liệu sơ cấp cho quá trình tiến hóa là:",
        options: [
          "A. Đột biến.",
          "B. Chọn lọc tự nhiên.",
          "C. Giao phối không ngẫu nhiên.",
          "D. Các yếu tố ngẫu nhiên."
        ],
        correctAnswer: 0,
        explanation: "Đột biến (chủ yếu là đột biến gene) là nguồn nguyên liệu sơ cấp."
      },
      {
        id: "TN_57",
        type: "TN",
        title: "Câu 57 (TN). Tia UV có thể làm phát sinh đột biến gene theo cách nào sau đây?",
        options: [
          "A. Làm thay thế một cặp G – C bằng một cặp A – T.",
          "B. Làm mất 1 cặp G – C.",
          "C. Làm thay thế một cặp A – T bằng một cặp G – C.",
          "D. Làm cho 2 base Timin trên một mạch của DNA liên kết lại với nhau."
        ],
        correctAnswer: 3,
        explanation: "Tia UV làm 2 base T liền kề trên 1 mạch liên kết đồng hóa trị với nhau."
      },
      {
        id: "TN_61",
        type: "TN",
        title: "Câu 61 (TN). Base nitơ Guanin dạng hiếm (G*) kết cặp không đúng trong quá trình nhân đôi DNA có thể gây nên dạng đột biến gene nào?",
        options: [
          "A. Thay thế cặp A-T bằng cặp G-C.",
          "B. Thay thế cặp C-G bằng cặp A-T.",
          "C. Thay thế cặp G-C bằng cặp A-T.",
          "D. Thay thế cặp A-T bằng cặp C-G."
        ],
        correctAnswer: 2,
        explanation: "G* kết cặp với T qua nhân đôi dẫn đến thay thế cặp G-C bằng cặp A-T."
      },
      {
        id: "TN_62",
        type: "TN",
        title: "Câu 62 (TN). Nói về đột biến gene, phát biểu nào sau đây là đúng?",
        options: [
          "A. Đột biến gene chỉ liên quan đến một cặp nucleotide.",
          "B. Đột biến gene một khi đã phát sinh sẽ được truyền cho thế hệ sau.",
          "C. Đột biến gene có hại sẽ bị loại bỏ hoàn toàn khỏi quần thể.",
          "D. Đột biến gene có thể tạo ra allele mới trong quần thể."
        ],
        correctAnswer: 3,
        explanation: "D đúng vì đột biến tạo ra các alen mới. A sai vì có thể nhiều cặp; B sai do đột biến soma; C sai do alen lặn ẩn trong dị hợp."
      },
      {
        id: "TN_63",
        type: "TN",
        title: "Câu 63 (TN). Đột biến thay thế một cặp nucleotide ở vị trí số 9 tính từ mã mở đầu nhưng không làm xuất hiện mã kết thúc. Chuỗi polypeptide tương ứng do gene này tổng hợp:",
        options: [
          "A. Mất một acid amin ở vị trí thứ 3 trong chuỗi polypeptide.",
          "B. Có thể thay đổi một acid amin ở vị trí thứ 2 trong chuỗi polypeptide.",
          "C. Thay đổi một acid amin ở vị trí thứ 3 trong chuỗi polypeptide.",
          "D. Có thể thay đổi các acid amin từ vị trí thứ 2 về sau trong chuỗi polypeptide."
        ],
        correctAnswer: 2,
        explanation: "Vị trí nu số 9 nằm ở bộ ba thứ 3 tính từ mã mở đầu, do là đột biến thay thế nên làm thay đổi 1 amino acid ở vị trí thứ 3 này."
      },
      {
        id: "TN_65",
        type: "TN",
        title: "Câu 65 (TN). Hiện tượng đột biến ở vi khuẩn hình thành các chủng mới có khả năng kháng thuốc kháng sinh là ý nghĩa của đột biến gene đối với:",
        options: [
          "A. Tiến hóa.",
          "B. Chọn giống.",
          "C. Tạo giống.",
          "D. Nghiên cứu di truyền."
        ],
        correctAnswer: 0,
        explanation: "Thích nghi và tiến hóa trong môi trường có kháng sinh."
      },
      {
        id: "TN_66",
        type: "TN",
        title: "Câu 66 (TN). Chiếu xạ bào tử nấm để tạo chủng nấm Penicillium đột biến sản xuất penicillin có hoạt tính cao gấp 200 lần là ý nghĩa đối với:",
        options: [
          "A. Tiến hóa.",
          "B. Chọn giống.",
          "C. Nghiên cứu di truyền.",
          "D. Không có đáp án đúng."
        ],
        correctAnswer: 1,
        explanation: "Ứng dụng trong chọn tạo giống vi sinh vật sản xuất công nghiệp."
      },
      {
        id: "TN_67",
        type: "TN",
        title: "Câu 67 (TN). Đột biến làm thay đổi chiều xoắn của vỏ ốc khiến ốc đột biến không thể giao phối với ốc bình thường dẫn đến cách li sinh sản và hình thành loài mới là ý nghĩa đối với:",
        options: [
          "A. Tiến hóa.",
          "B. Chọn giống.",
          "C. Tạo giống.",
          "D. Nghiên cứu di truyền."
        ],
        correctAnswer: 0,
        explanation: "Cơ chế hình thành loài mới trong tiến hóa."
      },

      /* =========================================================================
         PHẦN 3: ĐÚNG / SAI LÝ THUYẾT (ĐS) - CỤM 4 Ý TỪ TÀI LIỆU
      ========================================================================= */
      {
        id: "DS_01",
        type: "DS",
        title: "Câu 1 (ĐS). Mỗi nhận định sau là đúng hay sai khi nói về đột biến gene?",
        subQuestions: [
          { key: "a", text: "Có thể có lợi, có hại hoặc trung tính.", correct: true },
          { key: "b", text: "Làm biến đổi cấu trúc của gene liên quan tới một cặp hoặc một số cặp nucleotide.", correct: true },
          { key: "c", text: "Làm nguyên liệu của quá trình chọn giống và tiến hoá.", correct: true },
          { key: "d", text: "Có thể làm cho sinh vật ngày càng đa dạng, phong phú.", correct: true }
        ],
        explanation: "Cả 4 nhận định đều chính xác theo định nghĩa và vai trò của đột biến gene."
      },
      {
        id: "DS_02",
        type: "DS",
        title: "Câu 2 (ĐS). Mỗi nhận định sau là đúng hay sai khi nói về đặc điểm của đột biến thay thế một cặp nucleotide?",
        subQuestions: [
          { key: "a", text: "Là một dạng đột biến điểm.", correct: true },
          { key: "b", text: "Chỉ liên quan tới một bộ ba.", correct: true },
          { key: "c", text: "Làm thay đổi trình tự nucleotide của nhiều bộ ba.", correct: false },
          { key: "d", text: "Dễ xảy ra hơn so với các dạng đột biến gene khác.", correct: true }
        ],
        explanation: "c sai vì đột biến thay thế 1 cặp nucleotide chỉ ảnh hưởng tới bộ ba có cặp nucleotide bị thay thế, không làm lệch khung đọc nhiều bộ ba."
      },
      {
        id: "DS_04",
        type: "DS",
        title: "Câu 4 (ĐS). Allele A ở vi khuẩn E. coli bị đột biến điểm thành allele a. Theo lí thuyết thì phát biểu nào đúng, phát biểu nào sai?",
        subQuestions: [
          { key: "a", text: "Nếu đột biến thay thế 1 cặp nucleotide ở vị trí giữa gene thì có thể làm thay đổi toàn bộ các bộ ba từ vị trí xảy ra đột biến cho đến cuối gene.", correct: false },
          { key: "b", text: "Chuỗi polypeptide do allele a và chuỗi polypeptide do allele A quy định có thể có trình tự amino acid giống nhau.", correct: true },
          { key: "c", text: "Nếu đột biến mất 1 cặp nucleotide thì allele a và allele A có chiều dài bằng nhau.", correct: false },
          { key: "d", text: "Allele a và allele A luôn luôn có số lượng nucleotide bằng nhau.", correct: false }
        ],
        explanation: "a sai vì thay thế chỉ làm thay đổi 1 bộ ba; b đúng do mã thoái hóa; c sai vì mất nucleotide làm gene ngắn đi; d sai vì thêm/mất làm số nu đổi."
      },
      {
        id: "DS_06",
        type: "DS",
        title: "Câu 6 (ĐS). Khi nói về đột biến gene thì mệnh đề nào đúng, mệnh đề nào sai?",
        subQuestions: [
          { key: "a", text: "Xét ở mức độ phân tử, phần nhiều đột biến điểm thường vô hại (trung tính).", correct: true },
          { key: "b", text: "Đột biến gene làm xuất hiện các allele khác nhau cung cấp nguyên liệu sơ cấp cho tiến hóa.", correct: true },
          { key: "c", text: "Mức độ gây hại của allele đột biến phụ thuộc vào điều kiện môi trường cũng như phụ thuộc vào tổ hợp gene.", correct: true },
          { key: "d", text: "Khi đột biến làm thay thế một cặp nucleotide trong gene luôn làm thay đổi trình tự amino acid trong chuỗi polypeptide.", correct: false }
        ],
        explanation: "d sai vì mã di truyền có tính thoái hóa (nhiều bộ ba cùng mã hóa 1 amino acid) nên thay thế có thể là đột biến đồng nghĩa."
      },
      {
        id: "DS_07",
        type: "DS",
        title: "Câu 7 (ĐS). Khi nói về đột biến gene thì mệnh đề nào đúng, mệnh đề nào sai?",
        subQuestions: [
          { key: "a", text: "Đột biến thay thế một cặp nucleotide có thể làm cho gene không được biểu hiện.", correct: true },
          { key: "b", text: "Đột biến làm giảm chiều dài của gene có thể làm tăng số amino acid của chuỗi polypeptide.", correct: true },
          { key: "c", text: "Đột biến thay thế cặp A - T bằng cặp G - C không thể làm cho bộ ba mã hóa amino acid trở thành bộ ba kết thúc.", correct: true },
          { key: "d", text: "Trong quá trình nhân đôi DNA, 1 phân tử 5-BU kết cặp với A của mạch khuôn thì luôn làm phát sinh đột biến gene.", correct: false }
        ],
        explanation: "a đúng nếu đột biến xảy ra ở promoter; b đúng nếu mất nu ở bộ ba kết thúc làm ribosome trượt tiếp đến bộ ba kết thúc sau; c đúng vì triplet kết thúc (ATT, ATC, ACT) không chứa G; d sai nếu 5-BU liên kết ở vùng DNA không mang gene."
      },
      {
        id: "DS_10",
        type: "DS",
        title: "Câu 10 (ĐS). Khi nói về đột biến gene thì mệnh đề nào đúng, mệnh đề nào sai?",
        subQuestions: [
          { key: "a", text: "Trong quần thể, giả sử gene A có 5 allele và có tác nhân 5BU tác động vào quá trình nhân đôi gene A thì làm phát sinh allele mới.", correct: false },
          { key: "b", text: "Trong tế bào có 1 allele đột biến, trải qua quá trình phân bào thì allele đột biến luôn di truyền về tế bào con.", correct: true },
          { key: "c", text: "Đột biến thay thế một cặp nucleotide vẫn có thể làm tăng số amino acid của chuỗi polypeptide.", correct: true },
          { key: "d", text: "Tác nhân 5BU tác động gây đột biến gene thì có thể sẽ làm tăng chiều dài của gene.", correct: false }
        ],
        explanation: "5-BU chỉ gây thay thế cặp A-T thành G-C nên không làm tăng chiều dài gene (d sai). Đột biến thay thế biến bộ ba kết thúc thành bộ ba mã hóa làm tăng chiều dài chuỗi polypeptide (c đúng)."
      },
      {
        id: "DS_11",
        type: "DS",
        title: "Câu 11 (ĐS). Gây đột biến mất 1 cặp nucleotide giữa vùng mã hoá của gene Z trong operon Lac của vi khuẩn E.coli. Mỗi mệnh đề dưới đây là đúng hay sai?",
        subQuestions: [
          { key: "a", text: "Sản phẩm của các gene Y, A có thể bị mất hoạt tính.", correct: false },
          { key: "b", text: "Gene Z nhân đôi 2 lần thì gene A cũng nhân đôi 2 lần.", correct: true },
          { key: "c", text: "Khi môi trường có đường Lactose, các gene không được phiên mã.", correct: false },
          { key: "d", text: "Số lần phiên mã của gene Z có thể nhiều hơn số lần phiên mã của gene Y.", correct: false }
        ],
        explanation: "Các gene cấu trúc Z, Y, A chung operon nên nhân đôi và phiên mã số lần bằng nhau. Mất nu ở vùng mã hóa gene Z chỉ làm hỏng protein Z, không ảnh hưởng Y và A."
      },
      {
        id: "DS_15",
        type: "DS",
        title: "Câu 15 (ĐS). Mỗi nhận định sau là đúng hay sai khi nói về đột biến gene?",
        subQuestions: [
          { key: "a", text: "Đột biến là nguồn nguyên liệu sơ cấp của tiến hoá.", correct: true },
          { key: "b", text: "Phần lớn các đột biến tự nhiên có hại cho cơ thể sinh vật.", correct: true },
          { key: "c", text: "Chỉ có những đột biến có lợi mới trở thành nguyên liệu cho quá trình tiến hoá.", correct: false },
          { key: "d", text: "Áp lực của quá trình đột biến biểu hiện ở tốc độ biến đổi tần số tương đối của allele.", correct: true }
        ],
        explanation: "c sai vì cả đột biến có hại và trung tính đều có thể trở thành nguyên liệu có lợi khi môi trường hoặc tổ hợp gene biến đổi."
      },
      {
        id: "DS_16",
        type: "DS",
        title: "Câu 16 (ĐS). Mỗi nhận định sau là đúng hay sai khi nói về nguyên nhân của các bệnh di truyền ở người?",
        subQuestions: [
          { key: "a", text: "Gene đột biến làm thay đổi một amino acid này bằng một amino acid khác nhưng không làm thay đổi chức năng của protein.", correct: false },
          { key: "b", text: "Gene bị đột biến dẫn đến protein được tổng hợp nhưng bị thay đổi chức năng.", correct: true },
          { key: "c", text: "Gene bị đột biến dẫn đến protein không được tổng hợp.", correct: true },
          { key: "d", text: "Gene bị đột biến làm tăng hoặc giảm số lượng protein.", correct: true }
        ],
        explanation: "a sai vì nếu chức năng protein không đổi (đột biến trung tính) thì không gây bệnh di truyền."
      },
      {
        id: "DS_27",
        type: "DS",
        title: "Câu 27 (ĐS). Một gene của nấm men bị đột biến điểm ở trong vùng mã hóa. mRNA sơ khai của hai gene bằng nhau, nhưng polypeptide đột biến ngắn hơn bình thường. Phát biểu nào đúng hay sai?",
        subQuestions: [
          { key: "a", text: "Đột biến đã xảy ra là đột biến mất một số cặp nucleotide.", correct: false },
          { key: "b", text: "Nguyên nhân có thể là do đột biến làm xuất hiện bộ ba kết thúc sớm.", correct: true },
          { key: "c", text: "Có thể so sánh chiều dài mRNA trưởng thành của 2 gene để xác định nguyên nhân.", correct: true },
          { key: "d", text: "Không có cách nào để xác định chính xác nguyên nhân làm cho chuỗi polypeptide của gene đột biến bị ngắn lại.", correct: false }
        ],
        explanation: "a sai vì mRNA sơ khai bằng nhau chứng tỏ là đột biến thay thế; c đúng vì nếu mRNA trưởng thành bằng nhau thì do codon kết thúc sớm, nếu ngắn hơn thì do đột biến vị trí nhận biết intron làm mất exon."
      }
    ];

    let currentQuestions = [...questionBank];

    // RENDER RA GIAO DIỆN
    function renderQuiz() {
      const filter = document.getElementById('filterType').value;
      const container = document.getElementById('quizContainer');
      document.getElementById('scoreDisplay').innerText = "Hoàn thành bài làm rồi nhấn 'Nộp bài & Chấm điểm'.";
      document.getElementById('scoreDisplay').className = "font-bold text-slate-800 text-base";
      container.innerHTML = '';

      const list = filter === 'ALL' ? currentQuestions : currentQuestions.filter(q => q.type === filter);
      document.getElementById('statBadge').innerText = `${list.length} câu`;

      if (list.length === 0) {
        container.innerHTML = '<div class="p-8 text-center text-slate-400 bg-white rounded-xl">Không tìm thấy câu hỏi phù hợp.</div>';
        return;
      }

      list.forEach((q, idx) => {
        let contentHtml = '';

        // 1. TỰ LUẬN NGẮN (TLN)
        if (q.type === 'TLN') {
          contentHtml = `
            <div class="mt-3 space-y-2">
              <div class="flex flex-col sm:flex-row gap-2">
                <input type="text" id="ans_${q.id}" placeholder="Gõ câu trả lời ngắn của bạn..." class="flex-1 p-2.5 text-sm bg-slate-50 border border-slate-300 rounded-xl focus:bg-white outline-indigo-500 font-medium">
                <button type="button" onclick="toggleHint('${q.id}')" class="text-xs bg-slate-100 hover:bg-slate-200 text-slate-600 px-3.5 py-2 rounded-xl transition font-semibold">💡 Gợi ý</button>
              </div>
              <div id="hint_${q.id}" class="text-xs text-amber-800 bg-amber-50 p-2.5 rounded-lg border border-amber-200 hidden font-medium">
                Gợi ý: ${q.hint}
              </div>
            </div>
          `;
        }
        // 2. TRẮC NGHIỆM (TN)
        else if (q.type === 'TN') {
          contentHtml = `
            <div class="grid grid-cols-1 md:grid-cols-2 gap-2.5 mt-3">
              ${q.options.map((opt, i) => `
                <label class="flex items-center gap-2.5 p-3 rounded-xl border border-slate-200 bg-slate-50 hover:bg-indigo-50/50 cursor-pointer text-sm transition">
                  <input type="radio" name="ans_${q.id}" value="${i}" class="w-4 h-4 text-indigo-600 focus:ring-indigo-500">
                  <span class="font-medium text-slate-700">${opt}</span>
                </label>
              `).join('')}
            </div>
          `;
        } 
        // 3. ĐÚNG / SAI (ĐS)
        else if (q.type === 'DS') {
          contentHtml = `
            <div class="mt-3 overflow-hidden rounded-xl border border-slate-200 shadow-sm">
              <table class="w-full text-left text-sm">
                <thead class="bg-slate-100 text-slate-600 font-bold border-b border-slate-200">
                  <tr>
                    <th class="p-3">Mệnh đề nhận định</th>
                    <th class="p-3 w-16 text-center text-emerald-700">Đúng</th>
                    <th class="p-3 w-16 text-center text-rose-700">Sai</th>
                  </tr>
                </thead>
                <tbody class="divide-y divide-slate-200 bg-white font-medium">
                  ${q.subQuestions.map(sub => `
                    <tr class="hover:bg-slate-50/80">
                      <td class="p-3 text-slate-700"><span class="font-bold text-indigo-600 mr-1">${sub.key})</span>${sub.text}</td>
                      <td class="p-3 text-center">
                        <input type="radio" name="ans_${q.id}_${sub.key}" value="true" class="w-4 h-4 text-emerald-600">
                      </td>
                      <td class="p-3 text-center">
                        <input type="radio" name="ans_${q.id}_${sub.key}" value="false" class="w-4 h-4 text-rose-600">
                      </td>
                    </tr>
                  `).join('')}
                </tbody>
              </table>
            </div>
          `;
        }

        const typeLabel = q.type === 'TLN' ? 'Tự luận ngắn' : (q.type === 'TN' ? 'Trắc nghiệm' : 'Đúng / Sai');
        const badgeColor = q.type === 'TLN' ? 'bg-amber-100 text-amber-800' : (q.type === 'TN' ? 'bg-blue-100 text-blue-800' : 'bg-purple-100 text-purple-800');

        container.innerHTML += `
          <div class="bg-white p-5 md:p-6 rounded-2xl shadow-sm border border-slate-200" id="card_${q.id}">
            <div class="flex items-center gap-2 mb-2">
              <span class="text-xs px-2.5 py-0.5 rounded-full font-bold ${badgeColor}">${typeLabel}</span>
              <span class="text-xs text-slate-400 font-bold">#${q.id}</span>
            </div>
            <p class="font-bold text-slate-800 text-sm md:text-base leading-relaxed">${q.title}</p>
            ${contentHtml}
            <div id="feedback_${q.id}" class="mt-3 p-3.5 rounded-xl text-xs md:text-sm hidden leading-relaxed font-medium"></div>
          </div>
        `;
      });
    }

    // HIỆN GỢI Ý CÂU TLN
    function toggleHint(id) {
      const el = document.getElementById(`hint_${id}`);
      el.classList.toggle('hidden');
    }

    // ĐẢO CÂU HỎI
    function shuffleQuestions() {
      currentQuestions.sort(() => Math.random() - 0.5);
      renderQuiz();
    }

    // CHUẨN HÓA TEXT SO SÁNH
    function normalizeStr(str) {
      return str.toLowerCase().replace(/[\.,-\/#!$%\^&\*;:{}=\-_`~()]/g,"").replace(/\s+/g," ").trim();
    }

    // CHẤM ĐIỂM
    function gradeAll() {
      const filter = document.getElementById('filterType').value;
      const list = filter === 'ALL' ? currentQuestions : currentQuestions.filter(q => q.type === filter);
      let earnedPoints = 0;
      let maxPoints = 0;

      list.forEach(q => {
        const feedback = document.getElementById(`feedback_${q.id}`);
        feedback.classList.remove('hidden', 'bg-emerald-50', 'text-emerald-900', 'bg-rose-50', 'text-rose-900', 'bg-amber-50', 'text-amber-900');

        // Chấm TLN
        if (q.type === 'TLN') {
          maxPoints += 1;
          const userVal = normalizeStr(document.getElementById(`ans_${q.id}`).value || '');
          let isCorrect = false;

          if (userVal.length > 0) {
            isCorrect = q.answers.some(ans => {
              const normAns = normalizeStr(ans);
              return userVal.includes(normAns) || normAns.includes(userVal);
            });
          }

          if (isCorrect) earnedPoints += 1;

          feedback.innerHTML = `
            <div class="font-bold mb-1">${isCorrect ? '✅ Trả lời chính xác!' : '❌ Chưa chính xác hoặc câu trả lời chưa đầy đủ.'}</div>
            <div>Đáp án chuẩn cốt lõi: <strong class="text-indigo-700">${q.answers[0]}</strong></div>
            <div class="text-slate-500 mt-1 italic">${q.explanation}</div>
          `;
          feedback.classList.add(isCorrect ? 'bg-emerald-50' : 'bg-rose-50', isCorrect ? 'text-emerald-900' : 'text-rose-900');
        }

        // Chấm TN
        else if (q.type === 'TN') {
          maxPoints += 1;
          const checked = document.querySelector(`input[name="ans_${q.id}"]:checked`);
          const userVal = checked ? parseInt(checked.value) : -1;
          const isCorrect = userVal === q.correctAnswer;
          if (isCorrect) earnedPoints += 1;

          feedback.innerHTML = `
            <div class="font-bold mb-1">${isCorrect ? '✅ Bạn chọn đúng!' : '❌ Chưa chính xác.'}</div>
            <div>Đáp án đúng: <strong class="text-indigo-700">${q.options[q.correctAnswer]}</strong></div>
            <div class="text-slate-500 mt-1 italic">${q.explanation}</div>
          `;
          feedback.classList.add(isCorrect ? 'bg-emerald-50' : 'bg-rose-50', isCorrect ? 'text-emerald-900' : 'text-rose-900');
        }

        // Chấm ĐS
        else if (q.type === 'DS') {
          maxPoints += 1;
          let correctSubCount = 0;
          let detailResult = [];

          q.subQuestions.forEach(sub => {
            const checked = document.querySelector(`input[name="ans_${q.id}_${sub.key}"]:checked`);
            const userChoice = checked ? checked.value === 'true' : null;
            const ok = userChoice === sub.correct;
            if (ok) correctSubCount++;
            detailResult.push(`${sub.key}) ${sub.correct ? 'ĐÚNG' : 'SAI'}`);
          });

          const subScore = (correctSubCount * 0.25);
          earnedPoints += subScore;

          feedback.innerHTML = `
            <div class="font-bold mb-1">Kết quả: Đúng ${correctSubCount}/4 ý (+${subScore.toFixed(2)} điểm)</div>
            <div class="text-xs text-slate-700 mb-1">Đáp án chi tiết: <strong>${detailResult.join(' | ')}</strong></div>
            <div class="text-slate-500 italic">${q.explanation}</div>
          `;
          feedback.classList.add(correctSubCount === 4 ? 'bg-emerald-50' : (correctSubCount > 0 ? 'bg-amber-50' : 'bg-rose-50'));
          feedback.classList.add(correctSubCount === 4 ? 'text-emerald-900' : (correctSubCount > 0 ? 'text-amber-900' : 'text-rose-900'));
        }
      });

      const scoreEl = document.getElementById('scoreDisplay');
      scoreEl.innerHTML = `Điểm số của bạn: <span class="text-indigo-600 text-xl font-extrabold">${earnedPoints.toFixed(2)}</span> / ${maxPoints.toFixed(1)} điểm`;
    }

    // Tự động nạp danh sách ban đầu
    renderQuiz();
  </script>
</body>
</html>