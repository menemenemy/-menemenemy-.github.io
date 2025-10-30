<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>教育哲學考古題</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; }
        .question { margin-bottom: 20px; }
        .options { margin-left: 20px; }
        .analysis { display: none; background-color: #f0f0f0; padding: 10px; margin-top: 10px; }
        button { margin-top: 10px; margin-right: 10px; }
    </style>
</head>
<body>
    <h1>教育哲學考古題</h1>
    <p>以下是教育哲學的選擇題考古題示例（超過100題）。每次顯示10題。點擊「換題目」按鈕可隨機顯示另10題。選擇答案後，點擊「送出答案」可開新視窗顯示錯誤題目及正確答案。</p>
    <button onclick="changeQuestions()">換題目</button>
    <button onclick="submitAnswers()">送出答案</button>
    <div id="questions-container"></div>

    <script>
        const questions = [
            { 
                text: "有一天上課時，老師正在解說人體的構造，惠慈問了老師一個問題：「身體看起來應是物質性的東西，但心靈也是物質性的東西嗎？還是屬於非物質性的東西呢？身體與心靈相比較，哪一個較為根本呢？兩者如何互動？」就哲學領域而言，惠慈的問題一般被歸屬於哲學哪一部門的研究主題？",
                options: ["(A) 倫理學", "(B) 美學", "(C) 知識論", "(D) 形上學"],
                correct: "(D) 形上學",
                explanation: "無額外解釋。"
            },
            { 
                text: "從腦科學的角度，認為人的智慧在於神經連結的密度與速度，若要神經夠縝密，就要讓孩子多接觸新思維，之後才能觸類旁通。這種對智慧的說法，較接近何種心靈說？",
                options: ["(A) 心靈實體說", "(B) 心靈狀態說", "(C) 完形派心靈論", "(D) 唯物主義心靈論"],
                correct: "(D) 唯物主義心靈論",
                explanation: "無額外解釋。"
            },
            { 
                text: "台灣小學的讀經教育可對應西方何種心靈學說的教育理論？",
                options: ["(A) 心靈實體說", "(B) 心靈狀態說", "(C) 唯物主義心靈論", "(D) 實驗主義心靈論"],
                correct: "(A) 心靈實體說",
                explanation: "無額外解釋。"
            },
            { 
                text: "哪一種心靈學說否定心靈與意識的存在，其教育理論主張｢教育萬能｣，認為可以透過刺激反應的連結，而隨心所欲將兒童訓練成任何預期的個人？",
                options: ["(A) 實驗主義的心靈論", "(B) 唯物主義的心靈論", "(C) 心靈實體說", "(D) 完形派的心靈論"],
                correct: "(B) 唯物主義的心靈論",
                explanation: "無額外解釋。"
            },
            { 
                text: "小新向已經是癌症末期的母親謊稱這學期成績是班上第二名，以獲取母親的歡心。此一行為若由下列何種規範倫理學的觀點而言，是可以諒解的？",
                options: ["(A) 目的論", "(B) 義務論", "(C) 德行倫理學", "(D) 道德相對論"],
                correct: "(A) 目的論",
                explanation: "無額外解釋。"
            },
            { 
                text: "在以「教師道德觀」為主題的研習活動中，關於「道德」的涵義，林老師將其表述為：「道德乃是理性的人為了彼此的利益，在別人同樣也會遵循的前提之下，所採納的一套人我相待的規則。」林老師的道德觀最接近哪一種道德理論？",
                options: ["(A) 效益論", "(B) 心理利己論", "(C) 倫理利己論", "(D) 社會契約論"],
                correct: "(D) 社會契約論",
                explanation: "效益論：最大多數人的最大幸福。心理利己論 : 人的心理構造會驅使我們做對自己有利的事。倫理利己論：每個人都應該作對自己最有利的行為。社會契約：個人融入政治社會是透過一個相互同意的過程，當中，個人同意遵守共同的規則，並接受相應的義務。"
            },
            { 
                text: "洪老師在教學中以康德的美學觀來施教。下列何者最不可能是洪老師的美育觀？",
                options: ["(A) 「美感經驗」是一種純粹而無私的滿足，並無外在的利害考量", "(B) 美感教育除了認知領域的教學外，還需激發學生的「想像力」", "(C) 可運用「優美」的境界，撼動觀賞者心靈，使產生一種高揚的精神狀態", "(D) 可提升學生的審美能力，亦能陶養學生的人格，達成道德教育之目的"],
                correct: "(C) 可運用「優美」的境界，撼動觀賞者心靈，使產生一種高揚的精神狀態",
                explanation: "優美：可以直接掌握外物的形象。壯美：無窮無盡、不拘形式的美，達到理性層次的時候，才能體會什麼是「無限大」的崇高之感。"
            },
            { 
                text: "阿德勒（M. Adler）曾提出哪兩種「美」來說明「美感判斷」？",
                options: ["(A) 心情恬適的悠然之美；崇敬莊嚴的壯闊之美", "(B) 心情恬適的自然之美；崇敬莊嚴的社會之美", "(C) 立即滿足的物理之美；需知識領略的心理之美", "(D) 立即滿足的愉悅之美；需知識領略的讚賞之美"],
                correct: "(D) 立即滿足的愉悅之美；需知識領略的讚賞之美",
                explanation: "無額外解釋。"
            },
            { 
                text: "下列對於感官唯實論的教育主張，何者是正確的？",
                options: ["(A) 有關事物的文字知識應先於事物的直接知識", "(B) 強調古代經典作為學習內容的重要性", "(C) 柏拉圖（Plato）的教育思想屬之", "(D) 強調事物研究的科學態度，注重與現實生活事物的關連"],
                correct: "(D) 強調事物研究的科學態度，注重與現實生活事物的關連",
                explanation: "無額外解釋。"
            },
            { 
                text: "陳老師上課常常運用未加以查證的網路資料作為教材，且又講得頭頭是道，讓學生信以為真。陳老師以為網路流傳的知識就是真實的，這最接近培根（F. Bacon）所批判的哪種偶像謬誤？",
                options: ["(A) 種族偶像", "(B) 洞穴偶像", "(C) 市場偶像", "(D) 劇院偶像"],
                correct: "(C) 市場偶像",
                explanation: "無額外解釋。"
            },
            { 
                text: "心理學所謂的「酸葡萄」和「甜檸檬」現象，就心理分析的觀點，比較接近於何種自我防衛？",
                options: ["(A) 投射", "(B) 合理化", "(C) 轉移目標", "(D) 補償作用"],
                correct: "(B) 合理化",
                explanation: ""
            },
            { 
                text: "智力測驗常用來預測學生在課業成績的表現，課業成績就可以被用作智力測驗的何種項度？",
                options: ["(A) 效標", "(B) 標準參照", "(C) 輻合效度", "(D) 區辨效度"],
                correct: "(A) 效標",
                explanation: ""
            },
            { 
                text: "小明的第二次段考英語科考了60分，對照百分等級為65，意思是小明在假設為100個人的團體中贏過多少人？",
                options: ["(A) 35人", "(B) 40人", "(C) 60人", "(D) 65人"],
                correct: "(D) 65人",
                explanation: ""
            },
            { 
                text: "考試焦慮是屬於何種性質的焦慮？",
                options: ["(A) 情境性焦慮", "(B) 特質性焦慮", "(C) 氣質性焦慮", "(D) 普遍性焦慮"],
                correct: "(A) 情境性焦慮",
                explanation: ""
            },
            { 
                text: "有關正向心理學的觀點，下列敘述何者是不正確的?",
                options: ["(A) 正向心理學重視人性善良面", "(B) 正向心理學是探討現代的心理疾病", "(C) 關注的是個人心理健康", "(D) 研究對象是所有人"],
                correct: "(B) 正向心理學是探討現代的心理疾病",
                explanation: ""
            },
            { 
                text: "下列何者非為馬斯洛（Maslow）動機需求論的成長需求？",
                options: ["(A) 自尊需求", "(B) 知的需求", "(C) 美的需求", "(D) 自我實現"],
                correct: "(A) 自尊需求",
                explanation: ""
            },
            { 
                text: "柯柏格（Kohlberg）道德理論中，有關習俗道德期的發展，下列敘述何者不是正確的？",
                options: ["(A) 此階段兒童道德定義的觀點是從同儕合作觀點出發", "(B) 此階段兒童道德發展相當於皮亞傑（Piaget）自律道德階段", "(C) 此階段兒童都是以作自己愉快的事情為道德判斷", "(D) 此階段兒童在認知上已能設身處地為他人著想"],
                correct: "(C) 此階段兒童都是以作自己愉快的事情為道德判斷",
                explanation: ""
            },
            { 
                text: "對於低自尊及缺乏學習動機的學生，教師的教學策略為何？",
                options: ["(A) 運用工作分析法", "(B) 加速過度學習", "(C) 提供充份練習", "(D) 提供成功經驗"],
                correct: "(D) 提供成功經驗",
                explanation: ""
            },
            { 
                text: "根據測驗標準化程度區分，測驗有「標準化」及「非標準化」兩種。以下何者並非「標準化測驗」的特性？",
                options: ["(A) 由測驗專家根據測驗的編製程序而編成", "(B) 測驗有建立常模、信度、效度等資料", "(C) 測驗實施、計分和解釋，都有一定程序", "(D) 測驗結果，乃根據教學前所訂的標準加以解釋"],
                correct: "(D) 測驗結果，乃根據教學前所訂的標準加以解釋",
                explanation: ""
            },
            { 
                text: "對問題無法依既定法則循序處理，而憑個人經驗探索答案，稱為何種思維？",
                options: ["(A) 聚斂思維", "(B) 擴散思維", "(C) 定向思維", "(D) 試探思維"],
                correct: "(B) 擴散思維",
                explanation: ""
            },
            { 
                text: "有關教師期望的敘述何者是不正確的？",
                options: ["(A) 教師期望不同，教學行為自然不同", "(B) 教師的自我應驗預言即是比馬龍效應", "(C) 教師期望越高，學生成就越大", "(D) 教師宜避免對學生有負面期望，以免有礙學生的發展"],
                correct: "(C) 教師期望越高，學生成就越大",
                explanation: ""
            },
            { 
                text: "小名是習得無助感的學生，他通常會做何種歸因？",
                options: ["(A) 將成功歸因於能力，將失敗歸因為努力不夠", "(B) 將成功歸因於努力，將失敗歸因為能力不夠", "(C) 將成功歸因於努力，將失敗歸因為運氣不佳", "(D) 將成功歸因於能力，將失敗歸因為運氣不佳"],
                correct: "(B) 將成功歸因於努力，將失敗歸因為能力不夠",
                explanation: ""
            },
            { 
                text: "下列敘述中有關認知發展理論，何者是正確的？",
                options: ["(A) 行為學派認為人的認知結構是靠後天文化與學習歷程而建構", "(B) 皮亞傑（Piaget）認為學生的認知發展要經由教育促進其知識結構", "(C) 維高斯基（Vygotsky）認為學生是認知發展主動作用者，不是靠外在環境建構認知", "(D) 布魯納（Bruner）認為學生是被動求知者，但是教育不會加速其認知發展"],
                correct: "(A) 行為學派認為人的認知結構是靠後天文化與學習歷程而建構",
                explanation: ""
            },
            { 
                text: "卡泰爾與荷恩（Cattel & Horn）認為流體智力與晶體智力最大差別是",
                options: ["(A) 流體智力是解決抽象問題能力，晶體智力是解決具體問題能力", "(B) 流體智力是解決抽象問題能力，晶體智力是解決訊息處理技能", "(C) 流體智力是解決抽象問題能力，晶體智力是解決學業與生活經驗能力", "(D) 流體智力是普通能力，晶體智力是特殊能力"],
                correct: "(C) 流體智力是解決抽象問題能力，晶體智力是解決學業與生活經驗能力",
                explanation: ""
            },
            { 
                text: "為增加高焦慮學生的成就動機，老師宜採用那種方式？",
                options: ["(A) 增加教材的資料", "(B) 增加課程難度", "(C) 提高課程的結構性", "(D) 減少課程的結構性"],
                correct: "(C) 提高課程的結構性",
                explanation: ""
            },
            { 
                text: "有關自我發現式教學設計的研究，下列敘述何者是正確的？",
                options: ["(A) 發現式教學設計對中上資質學生是有效的", "(B) 對於可以達到自我實現的學生是有效的", "(C) 學生可藉以了解所選擇目標的理由，發展內在動機", "(D) 學生藉外在增強方式發展內在動機"],
                correct: "(C) 學生可藉以了解所選擇目標的理由，發展內在動機",
                explanation: ""
            },
            { 
                text: "依艾里克森（Erikson）的理論，青少年人格發展的關鍵為何？",
                options: ["(A) 自主行動對羞怯懷疑", "(B) 自動自發對退縮愧疚", "(C) 勤奮努力對自貶自抑", "(D) 自我統整對角色混淆"],
                correct: "(D) 自我統整對角色混淆",
                explanation: ""
            },
            { 
                text: "下列敘述何者是青春期學生的反思?",
                options: ["(A) 回到自我中心思考的現象", "(B) 對自己內心加以思考的能力", "(C) 自主性開始發展的現象", "(D) 與同儕合作達成共同目標的行為"],
                correct: "(B) 對自己內心加以思考的能力",
                explanation: ""
            },
            { 
                text: "下列何者為有目的性老師的特徵？",
                options: ["(A) 常會思考採取某教學行動的目的在哪裡", "(B) 常會思考學生表現某行動的目的在哪裡", "(C) 容易陷入學校人際紛爭", "(D) 容易表現逢迎行為"],
                correct: "(A) 常會思考採取某教學行動的目的在哪裡",
                explanation: ""
            },
            { 
                text: "老師想要改善課堂教學，增進學生的長期記憶，下列那一種策略是不適合的？",
                options: ["(A) 精緻化（elaboration）", "(B) 組織化（organization）", "(C) 脈絡化（context）", "(D) 複誦化（rehearsal）"],
                correct: "(C) 脈絡化（context）",
                explanation: ""
            },
            { 
                text: "有關專家與生手的敘述，何者正確？",
                options: ["(A) 能成為專家，是因為記憶力比生手好", "(B) 專家具有好的思考策略，而非因為擁有專門領域知識", "(C) 專家的思考策略可作為訓練生手的指導原則", "(D) 專家較常用前向式而非倒向式的解題策略"],
                correct: "(D) 專家較常用前向式而非倒向式的解題策略",
                explanation: ""
            },
            { 
                text: "檔案評量較一般紙筆測驗更能達成下列何種目的？",
                options: ["(A) 內容取樣夠廣", "(B) 呈現學生的學習歷程", "(C) 評分具客觀性", "(D) 呈現學生的表達能力"],
                correct: "(B) 呈現學生的學習歷程",
                explanation: ""
            },
            { 
                text: "下列對討論教學法的說明何者正確？",
                options: ["(A) 強調正確客觀的答案", "(B) 不宜討論具爭議性的問題，免得增加學生的困惑", "(C) 為避免錯誤學習，新奇或困難的題目不適合", "(D) 討論前需先確定學生是否具有足夠的先備知識"],
                correct: "(D) 討論前需先確定學生是否具有足夠的先備知識",
                explanation: ""
            },
            { 
                text: "下列敘述何者正確？",
                options: ["(A) 教師的回饋會影響學生的歸因風格", "(B) 競爭感的體認是學生追求成就的內在動力", "(C) 鼓勵學生抱持「避免失敗」的動機，才能讓學生感受較少威脅", "(D) 根據動機的期待理論來看，難度較高的作業，挑戰性愈高愈有助於提升學生的學習動機"],
                correct: "(A) 教師的回饋會影響學生的歸因風格",
                explanation: ""
            },
            { 
                text: "班杜拉（Bandura）指出觀察學習的四階段歷程為：",
                options: ["(A) 注意階段", "(B) 再生階段", "(C) 保持階段", "(D) 動機階段"],
                correct: "(B) 再生階段",
                explanation: ""
            },
            { 
                text: "斯普朗格（E.Spranger）的教育哲學強調教師應具備「教育愛」（diepädagogischeLiebe）。以下哪一項敘述才合乎斯普朗格所說的「教育愛」？",
                options: ["(A) 教育愛是老師像愛自己子女一樣的愛學生", "(B) 教育愛是老師基於學生具有價值創造之無限潛能，而全心全力奉獻教育工作", "(C) 教育愛是老師要像上帝愛所有世人一樣的愛所有的學生", "(D) 教育愛是教師把學生視為自己親兄弟一樣的愛護"],
                correct: "(B) 教育愛是老師基於學生具有價值創造之無限潛能，而全心全力奉獻教育工作",
                explanation: ""
            },
            { 
                text: "在柏拉圖（Plato）《共和國篇》（Republic）中的「洞穴隱喻」，掙脫枷鎖的囚徒出洞穴，享受陽光和自然之美後，又重返洞穴，想要拯救所有囚徒，走出洞穴之外。如果用理想的教師的圖像來解釋這位囚徒的行為，以下哪一種圖像最適合說明其所代表的教師圖像？",
                options: ["(A) 布伯（M.Buber）所說的教師應和學生合作共建平等的「我-汝」師生關係", "(B) 季胡（H.A.Giroux）所認為的教師應該成為轉化型的知識份子", "(C) 赫爾巴特（J.Fr.Herbart）所認為的教師必須是具有品格與專業知識的典範人格", "(D) 斯普朗格（E.Spranger）所認為的教師應該是傳統價值的繼承者與新價值的展開者"],
                correct: "(A) 布伯（M.Buber）所說的教師應和學生合作共建平等的「我-汝」師生關係",
                explanation: ""
            },
            { 
                text: "以下哪一項是進步主義（progressivism）和精粹主義（essentialism）有關課程內容選擇的最大差異？",
                options: ["(A) 進步主義主張課程應以「活動和經驗」為主；精粹主義主張課程內容應慎選人類文化的菁華", "(B) 進步主義主張依事實來選擇課程；精粹主義強調文化中的經典研讀", "(C) 進步主義強調課程的邏輯結構；精粹主義強調課程應含括永恆真理", "(D) 進步主義主張課程應合乎兒童興趣；精粹主義主張背誦經典著作"],
                correct: "(C) 進步主義強調課程的邏輯結構；精粹主義強調課程應含括永恆真理",
                explanation: ""
            },
            { 
                text: "依照柏拉圖（Plato）的美感教育理論，以下哪一類教材最適合選為音樂教材？",
                options: ["(A) 流行歌曲", "(B) 搖滾樂", "(C) 古典音樂", "(D) 爵士樂"],
                correct: "(A) 流行歌曲",
                explanation: ""
            },
            { 
                text: "依照哈伯瑪斯（J.Habermas）的溝通行動理論，教室中的生活公約最好以何種方式訂定？",
                options: ["(A) 由老師和學生共同參與，用理性論證的方式達到協議", "(B) 學生學生自行表決，以多數決決議公約內容", "(C) 學生提公約內容建議，由學生表決決定", "(D) 依照學校的校規來訂定"],
                correct: "(C) 學生提公約內容建議，由學生表決決定",
                explanation: ""
            },
            { 
                text: "修鐵窗工人對有點不放心的屋主說：「您不用擔心啦! 我修鐵窗是非常專業的!」從分析哲學的角度來了解，這裡所指的「專業」其真實的意義是下列何項？",
                options: ["(A) 具有專精的學術基礎", "(B) 修鐵窗是很獨特的行業", "(C) 是技術非常純熟", "(D) 對於社會能提供重大的服務"],
                correct: "(B) 修鐵窗是很獨特的行業",
                explanation: ""
            },
            { 
                text: "依程序論（Proceduralism）倫理學的原理來進行道德教學，應該強調以下哪一項重點？",
                options: ["(A) 強調道德實踐的順序性", "(B) 用理性討論的方法，讓學生分析道德規範的適切性", "(C) 激發學生的道德情感，使之付諸實踐", "(D) 要求學生嚴守道德規範"],
                correct: "(B) 用理性討論的方法，讓學生分析道德規範的適切性",
                explanation: ""
            },
            { 
                text: "杜威 (J. Dewey) 曾在其著作《民主主義與教育》中，提到 人類幼稚期的兩大特性，以印證人類受教育的可能性。其 一為「依賴性」 ，另一為何？",
                options: ["(A) 獨特性", "(B) 組織性", "(C) 可塑性", "(D) 創造性"],
                correct: "(C) 可塑性",
                explanation: ""
            },
            { 
                text: "有關建構主義（ constructivism ）的敘述，下列何者 錯誤 ?",
                options: ["(A) 強調親自操作、活動為基礎的教與學", "(B) 教學以學習者為中心，以發展學童的思考架構", "(C) 鼓勵學生從事批判思考，而不是記憶和背誦", "(D) 主張學習是環境、行為與反應之間的關係"],
                correct: "(D) 主張學習是環境、行為與反應之間的關係",
                explanation: ""
            },
            { 
                text: "下列哪個教育哲學派別強調知識的原則是恆久的，重視個 體心靈的訓練，認為應以數學、邏輯、語言、經典著作等 課程為主？",
                options: ["(A) 實用主義", "(B) 存在主義", "(C) 精粹主義", "(D) 永恆主義"],
                correct: "(D) 永恆主義",
                explanation: ""
            },
            { 
                text: "個人接受社會上各種知識、技能、行為模式與價值觀念， 這種社會與個人相互感應與學習模仿的歷程，稱之為何？",
                options: ["(A) 同理心", "(B) 互動論", "(C) 結構化", "(D) 社會化"],
                correct: "(D) 社會化",
                explanation: ""
            },
            { 
                text: "根據皮亞傑 (J. Piaget) 的觀點， 融合新的經驗到已經建立的 認知結構中，這種發展過程稱之為何？",
                options: ["(A) 平衡 (equilibration)", "(B) 同化 (assimilation)", "(C) 調適 (accommodation)", "(D) 組織 (organization)"],
                correct: "(B) 同化 (assimilation)",
                explanation: ""
            },
            { 
                text: "下列哪些學者的主張被歸類為行為主義？甲、皮亞傑； 乙、維高斯基；丙、巴夫洛夫；丁、馬斯洛；戊、桑代克； 己、奧斯貝爾、庚、史肯納？",
                options: ["(A) 甲乙丁", "(B) 丙丁戊", "(C) 戊己庚", "(D) 丙戊庚"],
                correct: "(D) 丙戊庚",
                explanation: ""
            },
            { 
                text: "國民小學學校班級數在 24 至 48 班者，其輔導教師的員額 編制規定為何？",
                options: ["(A) 設置兼任輔導教師 1 名", "(B) 設置兼任輔導教師 2 名", "(C) 設置專任輔導教師 1 名，兼任輔導教師 1 名", "(D) 設置專任輔導教師 2 名"],
                correct: "(C) 設置專任輔導教師 1 名，兼任輔導教師 1 名",
                explanation: ""
            },
            { 
                text: "有關精粹主義 (essentialism) 教育理念的敘述，下列何者 錯 誤 ?",
                options: ["(A) 主張教育在傳遞人類社會文化遺產，培養良好社會公 民", "(B) 主張教學以兒童為中心，反對教師為中心的教學", "(C) 以理想主義 (idealism) 和唯實主義 (realism) 的思想為基 礎", "(D) 重視心智訓練、核心知識，課程以文學、外語、歷史、 宗教為主"],
                correct: "(B) 主張教學以兒童為中心，反對教師為中心的教學",
                explanation: ""
            },
            { 
                text: "根據艾瑞克森 (E. Erikson) 的心理社會發展理論，青春期的 青少年 (12 至 18 歲 ) 約處於哪一階段？",
                options: ["(A) 自動自發對羞恥懷疑", "(B) 積極對愧疚", "(C) 勤奮對自卑", "(D) 自我統整對角色混淆"],
                correct: "(D) 自我統整對角色混淆",
                explanation: ""
            },
            { 
                text: "從評量資料的解釋觀點而言，魏氏個別智力測驗 ( 第四版 ) 屬於何種評量？",
                options: ["(A) 形成性評量", "(B) 總結性評量", "(C) 常模參照評量", "(D) 標準參照評量"],
                correct: "(C) 常模參照評量",
                explanation: ""
            },
            { 
                text: "在教學過程中，教師將學習內容性質相近的主題，調整順 序、重組或相互配合施教，所形成的是何種課程？",
                options: ["(A) 活動課程", "(B) 廣域課程", "(C) 經驗課程", "(D) 相關課程"],
                correct: "(D) 相關課程",
                explanation: ""
            },
            { 
                text: "首先於 1763 年頒布普通鄉村學校法，規定五歲至十三歲 為強迫就學年齡，並規定家長未送其子女入學須受懲處， 開啟強迫入學風氣之先鋒的國家為何？",
                options: ["(A) 法國", "(B) 德國", "(C) 英國", "(D) 俄羅斯"],
                correct: "(B) 德國",
                explanation: ""
            },
            { 
                text: "李老師上課時以錯誤的網路資訊當教材，學生與家長事後 質問他，他面對質疑不願查證與認錯，是誤用了下列何種 教師權威？",
                options: ["(A) 傳統世襲權威", "(B) 學術專業權威", "(C) 人格感召權威", "(D) 行政法理權威"],
                correct: "(B) 學術專業權威",
                explanation: ""
            },
            { 
                text: "英國教育哲學家皮德思 (R.S.Peters) 認為教育是價值傳遞 與創造的活動，並提出三項教育規準。下列何者 不是 他所 提出的教育規準？",
                options: ["(A) 合價值性", "(B) 合程序性", "(C) 合認知性", "(D) 合自願性"],
                correct: "(B) 合程序性",
                explanation: ""
            },
            { 
                text: "就教育的目的形式而言，可分為 「內在目的」 (intrinsic aim) 與「外在目的」 (extrinsic aim) 兩種。下列哪一項屬於教育 的「內在目的」？",
                options: ["(A) 培養社會有用公民", "(B) 強化愛國愛鄉意識", "(C) 培育國家政治人才", "(D) 培養學生健全人格"],
                correct: "(D) 培養學生健全人格",
                explanation: ""
            },
            { 
                text: "下述何種敘述較符合實用主義 (pragmatism) 的教育觀？",
                options: ["(A) 教育應幫助學生在民主社會中做好生活準備", "(B) 教育的作用在於傳遞人類社會文化遺產", "(C) 教師是「權威者」 ，強調傳統的講授法", "(D) 教育應幫助個體透過心靈來追求真理"],
                correct: "(A) 教育應幫助學生在民主社會中做好生活準備",
                explanation: ""
            },
            { 
                text: "下列何者 不是 協同教學的特色？",
                options: ["(A) 單純有效的班級管理", "(B) 彈性多元的教學模式", "(C) 分工合作的專業對話", "(D) 學生學習的個別適應"],
                correct: "(A) 單純有效的班級管理",
                explanation: ""
            },
            { 
                text: "胡老師在教梯形面積時，未直接告訴學生梯形面積公式， 而是提供每組學生兩個相同的梯形，請學生運用教具，透 過分組討論、填寫學習單，最後請各組學生共同歸納，找 出梯形面積和拼組出的平行四邊形 ( 含長方形 ) 之間的關 係，再推導出梯形的面積公式。請問胡老師的教學設計較 接近哪一種理論？",
                options: ["(A) 內隱學習 (implicit learning)", "(B) 精熟學習 (mastery learning)", "(C) 探究學習 (inquiry learning)", "(D) 情境學習 (situational learning)"],
                correct: "(C) 探究學習 (inquiry learning)",
                explanation: ""
            },
            { 
                text: "下列哪位學者主張道德教育應注重學生在面對道德問題 的價值判斷，並將道德認知發展順序分為「三時期六階 段」？",
                options: ["(A) 柯爾伯格 (L. Kohlberg)", "(B) 皮亞傑 (J. Piaget)", "(C) 杜威 (J. Dewey)", "(D) 笛卡兒 (R. Descartes)"],
                correct: "(A) 柯爾伯格 (L. Kohlberg)",
                explanation: ""
            },
            { 
                text: "下列哪位學者特別強調個體的學習得自於觀察與模仿的 作用？",
                options: ["(A) 柯爾伯格 (L. Kohlberg)", "(B) 桑代克 (E. L. Thorndike)", "(C) 班杜拉 (A. Bandura)", "(D) 史金納 (B. F. Skinner)"],
                correct: "(C) 班杜拉 (A. Bandura)",
                explanation: ""
            },
            { 
                text: "根據班杜拉 (A. Bandura) 的社會學習論，學習者經由觀察 學習對楷模人物的行為進行模仿時，將因學習者當時的心 理需求與學習所得的不同，而有四種不同的方式，以下何 者 不是 其觀點？",
                options: ["(A) 直接模仿 (direct modeling)", "(B) 間接模仿 (indirect modeling)", "(C) 象徵模仿 (symbolic modeling)", "(D) 抽象模仿 (abstract modeling)"],
                correct: "(B) 間接模仿 (indirect modeling)",
                explanation: ""
            },
            { 
                text: "從班杜拉 (A. Bandura) 的社會學習論觀點，下列何者是兒 童最喜歡模仿的對象？",
                options: ["(A) 與兒童不同性別的人", "(B) 出身低階層社會", "(C) 心目中最重要的人", "(D) 同儕團體內的弱勢者"],
                correct: "(C) 心目中最重要的人",
                explanation: ""
            },
            { 
                text: "下列何者 不是 班杜拉 (A. Bandura) 所提出的觀察學習四階 段歷程觀點？",
                options: ["(A) 注意階段 (attentional phase)", "(B) 反省階段 (reflecting phase)", "(C) 再生階段 (reproduction phase)", "(D) 動機階段 (motivational phase)"],
                correct: "(B) 反省階段 (reflecting phase)",
                explanation: ""
            },
            { 
                text: "下列有關學者與其理論的對應敘述，何者 錯誤 ？",
                options: ["(A) 皮亞傑 (J. Piaget) — 認知發展階段論", "(B) 維果茨基 (L. S. Vygotsky) — 近側發展區", "(C) 馬斯洛 (A. H. Maslow) — 人本主義心理學", "(D) 史金納 (B. F. Skinner) — 精熟學習論"],
                correct: "(D) 史金納 (B. F. Skinner) — 精熟學習論",
                explanation: ""
            },
            { 
                text: "下列有關學者與其理論的對應敘述，何者正確？",
                options: ["(A) 史金納 (B. F. Skinner) — 螺旋式課程", "(B) 蓋聶 (G.Gagne) — 道德發展三期六段論", "(C) 奧蘇貝爾 (D. P. Ausubel ) — 意義學習論", "(D) 埃金森 (R. C. Atkinson) — 社會學習理論"],
                correct: "(C) 奧蘇貝爾 (D. P. Ausubel ) — 意義學習論",
                explanation: ""
            },
            { 
                text: "兒童開始以具體事例為基礎進行邏輯推理，並能從事物的 分類、比較以了解其間的關係，是屬於 J. Piaget 認知發展 論的哪個階段？",
                options: ["(A) 感覺動作期", "(B) 具體運思期", "(C) 運思預備期", "(D) 形式運思期"],
                correct: "(B) 具體運思期",
                explanation: ""
            },
            { 
                text: "兒童運用感官事物所得的心像，了解周圍的世界，例如可 以憑記憶說出某種東西的形像樣貌，做為思考的輔助，這 是 Bruner 表徵系統論的哪一種表徵方式？",
                options: ["(A) 動作表徵", "(B) 形像表徵", "(C) 符號表徵", "(D) 形式表徵"],
                correct: "(B) 形像表徵",
                explanation: ""
            },
            { 
                text: "美國心理學家 Erikson 提出心理社會發展論，將人格發展 分為八個時期，國小階段的兒童屬於哪個時期？",
                options: ["(A) 勤奮努力、自貶自卑。", "(B) 友愛親密、孤獨疏離。", "(C) 自動自發、退縮內疚。", "(D) 對人信賴、不信賴人。"],
                correct: "(A) 勤奮努力、自貶自卑。",
                explanation: ""
            },
            { 
                text: "Thorndike 用貓開啟迷籠實驗，提出學習三個定律，其中 個體反應後獲得滿足者，反應將被強化，刺激反應之間聯 結加強，反之，無效果之反應將逐漸減弱，這是描述哪一 個定律？",
                options: ["(A) 練習律", "(B) 準備律", "(C) 聯結律", "(D) 效果律"],
                correct: "(D) 效果律",
                explanation: ""
            },
            { 
                text: "在制約學習中，刺激反應間發生聯結之後，如增強停止， 制約反應之間強度將逐漸減低，最後終將停止，這是學習 歷程中的哪個現象？",
                options: ["(A) 消弱", "(B) 次增強", "(C) 增強", "(D) 類化"],
                correct: "(A) 消弱",
                explanation: ""
            },
            { 
                text: "個體以既有的認知基模去適應環境的新要求，企圖以此種 方式把新經驗納入舊經驗之中，此種現象，稱為什麼？",
                options: ["(A) 調適", "(B) 同化", "(C) 類比", "(D) 平衡"],
                correct: "(B) 同化",
                explanation: ""
            },
            { 
                text: "先後學到新舊兩種經驗，當你要回憶新經驗時，舊經驗產 生干擾作用，這種干擾稱為？",
                options: ["(A) 倒攝抑制", "(B) 學習遷移", "(C) 順攝抑制", "(D) 學後保留"],
                correct: "(A) 倒攝抑制",
                explanation: ""
            },
            { 
                text: "描述前後幾次測驗所得的結果是否一致的程度，稱為？",
                options: ["(A) 效度", "(B) 準度", "(C) 效標", "(D) 信度"],
                correct: "(D) 信度",
                explanation: ""
            },
            { 
                text: "在舉行測驗之後，將每個學生的分數拿來與同質類的學生 或其所屬群體之得分或平均數相比較，這種測驗稱為？",
                options: ["(A) 常模參照測驗", "(B) 標準參照測驗", "(C) 標準化測驗", "(D) 特殊性向測驗"],
                correct: "(A) 常模參照測驗",
                explanation: ""
            },
            { 
                text: "教育需合於受教者身心發展歷程，此為教育的哪一個規 準？",
                options: ["(A) 合價值性", "(B) 合認知性", "(C) 合自願性", "(D) 合程序性"],
                correct: "(B) 合認知性",
                explanation: ""
            },
            { 
                text: "有關哲學與科學，何者為非",
                options: ["(A)科學的產生是受到哲學的指引", "(B)哲學有助於不同學術的溝通與統整", "(C)科學的發展有賴哲學的價值判斷", "(D)哲學研究目的不是解決問題，而是建立理論"],
                correct: "(D)哲學研究目的不是解決問題，而是建立理論",
                explanation: ""
            },
            { 
                text: "提出歸納法",
                options: ["(A)Bacon", "(B)Comenius", "(C)Locke", "(D)Rousseau"],
                correct: "(A)Bacon",
                explanation: ""
            },
            { 
                text: "批判四大偶像",
                options: ["(A)Bacon", "(B)Comenius", "(C)Locke", "(D)Rousseau", "(E)Herbart"],
                correct: "(A)Bacon",
                explanation: ""
            },
            { 
                text: "提倡泛智主義，感官教學",
                options: ["(A)Bacon", "(B)Comenius", "(C)Locke", "(D)Rousseau"],
                correct: "(B)Comenius",
                explanation: ""
            },
            { 
                text: "主張身先於心",
                options: ["(A)Bacon", "(B)Comenius", "(C)Locke", "(D)Rousseau"],
                correct: "(C)Locke",
                explanation: ""
            },
            { 
                text: "提出統覺論和四段教學法",
                options: ["(A)Bacon", "(B)Comenius", "(C)Locke", "(D)Rousseau", "(E)Herbart"],
                correct: "(E)Herbart",
                explanation: ""
            },
            { 
                text: "從倫理學與心理學基礎上來建立教育科學",
                options: ["(A)Bacon", "(B)Comenius", "(C)Locke", "(D)Rousseau", "(E)Herbart"],
                correct: "(E)Herbart",
                explanation: ""
            },
            { 
                text: "認為教育是文化複製",
                options: ["(A)Rousseau", "(B)Herbart", "(C)Spranger", "(D)Bourdieu"],
                correct: "(D)Bourdieu",
                explanation: ""
            },
            { 
                text: "個人本位學者，認為教育的本質在開展一個人的無限可能性，並協助個人自我實現，教育應該以兒童為中心",
                options: ["(A)Dewey", "(B)Kerschensteiner", "(C)Fichte", "(D)Spencer", "(E)Giroux"],
                correct: "(A)Dewey",
                explanation: ""
            },
            { 
                text: "社會本位學者，認為教育的本質是使個人的價值觀與行為模式能夠符合社會規範",
                options: ["(A) Rousseau", "(B)Kerschensteiner", "(C)Spencer", "(D)Giroux"],
                correct: "(B)Kerschensteiner",
                explanation: ""
            },
            { 
                text: "教育的目的之一是要啟示學生對人生意義的掌握。西洋哲學中那位學者認為善即快樂，人生的意義在於追求快樂？",
                options: ["(A)亞里斯多德", "(B)柏拉圖", "(C)齊諾(Zeno)", "(D)伊璧鳩魯(Epicurus)"],
                correct: "(D)伊璧鳩魯(Epicurus)",
                explanation: ""
            },
            { 
                text: "著《共和國》",
                options: ["(A)Socrates", "(B)Plato", "(C)Aristotle", "(D)Descartes", "(E)Hegel"],
                correct: "(B)Plato",
                explanation: ""
            },
            { 
                text: "提出四因說",
                options: ["(A)Socrates", "(B)Plato", "(C)Aristotle", "(D)Descartes", "(E)Hegel"],
                correct: "(C)Aristotle",
                explanation: ""
            },
            { 
                text: "提出「我思故我在」",
                options: ["(A)Socrates", "(B)Plato", "(C)Aristotle", "(D)Descartes", "(E)Hegel"],
                correct: "(D)Descartes",
                explanation: ""
            },
            { 
                text: "提出歷史辯證法",
                options: ["(A)Socrates", "(B)Plato", "(C)Aristotle", "(D)Descartes", "(E)Hegel"],
                correct: "(E)Hegel",
                explanation: ""
            },
            { 
                text: "下列有關永恆主義的教育主張，何者錯誤？",
                options: ["(A) 知識是恆常的", "(B) 課程應以人文學科為主", "(C) 教師是知識的傳授者", "(D) 強調學生主動學習"],
                correct: "(D) 強調學生主動學習",
                explanation: ""
            },
            { 
                text: "存在主義教育哲學強調何者？",
                options: ["(A) 社會規範", "(B) 個人自由選擇", "(C) 傳統價值", "(D) 科學方法"],
                correct: "(B) 個人自由選擇",
                explanation: ""
            },
            { 
                text: "下列何者為精粹主義的教育目標？",
                options: ["(A) 培養批判思考", "(B) 傳遞核心知識", "(C) 強調經驗學習", "(D) 促進個人成長"],
                correct: "(B) 傳遞核心知識",
                explanation: ""
            },
            { 
                text: "杜威的教育哲學屬於哪一派？",
                options: ["(A) 永恆主義", "(B) 進步主義", "(C) 精粹主義", "(D) 存在主義"],
                correct: "(B) 進步主義",
                explanation: ""
            },
            { 
                text: "維高斯基強調的學習理論為何？",
                options: ["(A) 行為主義", "(B) 認知發展", "(C) 社會文化理論", "(D) 人本主義"],
                correct: "(C) 社會文化理論",
                explanation: ""
            },
            { 
                text: "近側發展區的概念是由誰提出？",
                options: ["(A) 皮亞傑", "(B) 維高斯基", "(C) 艾瑞克森", "(D) 馬斯洛"],
                correct: "(B) 維高斯基",
                explanation: ""
            },
            { 
                text: "馬斯洛需求階層的最頂端為何？",
                options: ["(A) 生理需求", "(B) 安全需求", "(C) 自尊需求", "(D) 自我實現"],
                correct: "(D) 自我實現",
                explanation: ""
            },
            { 
                text: "柯柏格道德發展階段的最後階段為何？",
                options: ["(A) 前習俗階段", "(B) 習俗階段", "(C) 後習俗階段", "(D) 自律階段"],
                correct: "(C) 後習俗階段",
                explanation: ""
            },
            { 
                text: "行為主義的代表人物為何？",
                options: ["(A) 皮亞傑", "(B) 史金納", "(C) 杜威", "(D) 羅傑斯"],
                correct: "(B) 史金納",
                explanation: ""
            },
            { 
                text: "人本主義教育強調何者？",
                options: ["(A) 知識傳授", "(B) 學生中心", "(C) 紀律訓練", "(D) 標準化測試"],
                correct: "(B) 學生中心",
                explanation: ""
            },
            { 
                text: "批判教育學的代表人物為何？",
                options: ["(A) 弗雷勒", "(B) 杜威", "(C) 柏拉圖", "(D) 亞里斯多德"],
                correct: "(A) 弗雷勒",
                explanation: ""
            },
            { 
                text: "後現代主義教育強調何者？",
                options: ["(A) 絕對真理", "(B) 多樣性與相對性", "(C) 傳統價值", "(D) 權威教學"],
                correct: "(B) 多樣性與相對性",
                explanation: ""
            },
            { 
                text: "理想主義的教育目標為何？",
                options: ["(A) 實用技能", "(B) 心靈發展", "(C) 社會適應", "(D) 經濟競爭"],
                correct: "(B) 心靈發展",
                explanation: ""
            },
            { 
                text: "唯實主義強調教育應基於何者？",
                options: ["(A) 主觀經驗", "(B) 客觀事實", "(C) 情感培養", "(D) 想像力"],
                correct: "(B) 客觀事實",
                explanation: ""
            },
            { 
                text: "實用主義認為知識應如何獲得？",
                options: ["(A) 權威傳授", "(B) 經驗驗證", "(C) 邏輯推理", "(D) 直覺洞察"],
                correct: "(B) 經驗驗證",
                explanation: ""
            },
            { 
                text: "存在主義主張教育應幫助學生何者？",
                options: ["(A) 適應社會", "(B) 自我實現", "(C) 學習經典", "(D) 發展技能"],
                correct: "(B) 自我實現",
                explanation: ""
            },
            { 
                text: "重建主義的教育目的是何？",
                options: ["(A) 維持現狀", "(B) 社會變革", "(C) 個人發展", "(D) 知識傳承"],
                correct: "(B) 社會變革",
                explanation: ""
            },
            { 
                text: "下列何者為皮亞傑認知發展的階段？",
                options: ["(A) 感覺運動期", "(B) 前運算期", "(C) 具體運算期", "(D) 以上皆是"],
                correct: "(D) 以上皆是",
                explanation: ""
            },
            { 
                text: "艾瑞克森人格發展階段中，嬰兒期為何？",
                options: ["(A) 信任 vs 不信任", "(B) 自主 vs 羞愧", "(C) 主動 vs 內疚", "(D) 勤奮 vs 自卑"],
                correct: "(A) 信任 vs 不信任",
                explanation: ""
            },
            { 
                text: "班杜拉的社會學習理論強調何者？",
                options: ["(A) 觀察學習", "(B) 操作制約", "(C) 古典制約", "(D) 認知發展"],
                correct: "(A) 觀察學習",
                explanation: ""
            },
            { 
                text: "奧蘇貝爾的意義學習強調何者？",
                options: ["(A) 機械背誦", "(B) 連結既有知識", "(C) 行為強化", "(D) 情感培養"],
                correct: "(B) 連結既有知識",
                explanation: ""
            },
            { 
                text: "布魯納的發現學習主張何者？",
                options: ["(A) 教師講授", "(B) 學生主動探索", "(C) 標準化課程", "(D) 競爭評量"],
                correct: "(B) 學生主動探索",
                explanation: ""
            },
            // 繼續添加其他獨特題目以確保超過100題
        ];

        let currentQuestions = [];

        function displayQuestions() {
            const container = document.getElementById('questions-container');
            container.innerHTML = '';
            for (let i = 0; i < 10; i++) {
                const q = currentQuestions[i];
                const div = document.createElement('div');
                div.className = 'question';
                div.innerHTML = `
                    <h3>題目 ${i + 1}:</h3>
                    <p>${q.text}</p>
                    <div class="options">
                        ${q.options.map(opt => `<label><input type="radio" name="q${i}" value="${opt}">${opt}</label><br>`).join('')}
                    </div>
                `;
                container.appendChild(div);
            }
        }

        function changeQuestions() {
            currentQuestions = [];
            const usedIndices = new Set();
            while (currentQuestions.length < 10) {
                const randomIndex = Math.floor(Math.random() * questions.length);
                if (!usedIndices.has(randomIndex)) {
                    usedIndices.add(randomIndex);
                    currentQuestions.push(questions[randomIndex]);
                }
            }
            displayQuestions();
        }

        function submitAnswers() {
            let errors = [];
            for (let i = 0; i < 10; i++) {
                const selected = document.querySelector(`input[name="q${i}"]:checked`);
                const q = currentQuestions[i];
                if (selected && selected.value !== q.correct) {
                    errors.push({
                        text: q.text,
                        options: q.options.join('\n'),
                        selected: selected.value,
                        correct: q.correct,
                        explanation: q.explanation
                    });
                } else if (!selected) {
                    errors.push({
                        text: q.text,
                        options: q.options.join('\n'),
                        selected: '未選擇',
                        correct: q.correct,
                        explanation: q.explanation
                    });
                }
            }

            let resultHtml = '<html><head><title>錯誤題目</title></head><body><h1>錯誤題目及正確答案</h1>';
            if (errors.length === 0) {
                resultHtml += '<p>全部正確！</p>';
            } else {
                errors.forEach((err, index) => {
                    const copyContent = `題目: ${err.text}\n選項:\n${err.options}\n您的選擇: ${err.selected}\n正確答案: ${err.correct}`;
                    const queryUrl = `https://www.google.com/search?q=${encodeURIComponent(err.text)}`;
                    const onclickScript = `navigator.clipboard.writeText('${copyContent.replace(/'/g, "\\'").replace(/\n/g, '\\n')}'); window.open('${queryUrl}', '_blank');`;
                    resultHtml += `<div><h3>錯誤題目 ${index + 1}:</h3><p>${err.text}</p><p><strong>您的選擇：</strong> ${err.selected}</p><p><strong>正確答案：</strong> ${err.correct}</p><button onclick="${onclickScript}">複製</button></div><hr>`;
                });
            }
            resultHtml += '</body></html>';

            const newWindow = window.open();
            newWindow.document.write(resultHtml);
            newWindow.document.close();
        }

        // Initial questions
        changeQuestions();
    </script>
</body>
</html>
