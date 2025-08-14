<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>부전연합역지구 - 건의사항 시스템</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Malgun Gothic', sans-serif;
            line-height: 1.6;
            color: #333;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            text-align: center;
        }

        .header h1 {
            color: #2c3e50;
            font-size: 2.2em;
            margin-bottom: 10px;
            font-weight: bold;
        }

        .header h2 {
            color: #3498db;
            font-size: 1.4em;
            margin-bottom: 15px;
        }

        .header p {
            color: #7f8c8d;
            font-size: 1.1em;
        }

        .main-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-bottom: 30px;
        }

        .suggestion-form {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }

        .suggestion-list {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }

        .form-title {
            color: #2c3e50;
            font-size: 1.5em;
            margin-bottom: 20px;
            font-weight: bold;
            display: flex;
            align-items: center;
        }

        .form-title::before {
            content: "✏️";
            margin-right: 10px;
            font-size: 1.2em;
        }

        .form-group {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            color: #2c3e50;
            font-weight: 600;
        }

        input[type="text"], 
        input[type="email"], 
        input[type="tel"], 
        select, 
        textarea {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #e0e6ed;
            border-radius: 12px;
            font-size: 16px;
            transition: all 0.3s ease;
            background: #fff;
        }

        input:focus, 
        select:focus, 
        textarea:focus {
            outline: none;
            border-color: #3498db;
            box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.1);
        }

        textarea {
            min-height: 120px;
            resize: vertical;
        }

        .submit-btn {
            background: linear-gradient(45deg, #3498db, #2980b9);
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 12px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            width: 100%;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(52, 152, 219, 0.4);
        }

        .suggestion-item {
            background: #f8f9fa;
            border-left: 4px solid #3498db;
            margin-bottom: 20px;
            padding: 20px;
            border-radius: 8px;
            transition: all 0.3s ease;
        }

        .suggestion-item:hover {
            background: #e3f2fd;
            transform: translateX(5px);
        }

        .suggestion-header {
            display: flex;
            justify-content: between;
            align-items: center;
            margin-bottom: 10px;
        }

        .category-badge {
            background: #3498db;
            color: white;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
        }

        .date-badge {
            background: #95a5a6;
            color: white;
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            margin-left: 10px;
        }

        .status-badge {
            padding: 4px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            margin-left: auto;
        }

        .status-pending {
            background: #f39c12;
            color: white;
        }

        .status-reviewing {
            background: #9b59b6;
            color: white;
        }

        .status-completed {
            background: #27ae60;
            color: white;
        }

        .suggestion-title {
            font-size: 1.1em;
            font-weight: 600;
            color: #2c3e50;
            margin-bottom: 8px;
        }

        .suggestion-content {
            color: #555;
            line-height: 1.5;
        }

        .stats-section {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .stat-card {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            transition: transform 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-5px);
        }

        .stat-number {
            font-size: 2.5em;
            font-weight: bold;
            margin-bottom: 5px;
        }

        .stat-label {
            font-size: 1em;
            opacity: 0.9;
        }

        @media (max-width: 768px) {
            .main-content {
                grid-template-columns: 1fr;
            }
            
            .header h1 {
                font-size: 1.8em;
            }
            
            .header h2 {
                font-size: 1.2em;
            }
        }

        .anonymous-check {
            display: flex;
            align-items: center;
            margin-top: 10px;
        }

        .anonymous-check input[type="checkbox"] {
            width: auto;
            margin-right: 10px;
        }

        .urgent-check {
            background: #fee;
            border: 1px solid #fcc;
            padding: 10px;
            border-radius: 8px;
            margin-top: 10px;
        }

        .urgent-check input[type="checkbox"] {
            width: auto;
            margin-right: 10px;
        }

        .admin-panel {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
            display: none;
        }

        .admin-toggle {
            position: fixed;
            top: 20px;
            right: 20px;
            background: #e74c3c;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 50px;
            cursor: pointer;
            font-size: 12px;
            z-index: 1000;
        }

        .admin-login {
            text-align: center;
            padding: 40px;
        }

        .admin-content {
            display: none;
        }

        .suggestion-manage {
            border: 1px solid #ddd;
            margin-bottom: 15px;
            padding: 20px;
            border-radius: 10px;
            background: #f9f9f9;
        }

        .suggestion-actions {
            display: flex;
            gap: 10px;
            margin-top: 15px;
            flex-wrap: wrap;
        }

        .action-btn {
            padding: 8px 15px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-size: 12px;
            font-weight: 600;
        }

        .btn-approve {
            background: #27ae60;
            color: white;
        }

        .btn-reject {
            background: #e74c3c;
            color: white;
        }

        .btn-complete {
            background: #3498db;
            color: white;
        }

        .btn-delete {
            background: #95a5a6;
            color: white;
        }

        .admin-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 15px;
            margin-bottom: 30px;
        }

        .admin-stat-card {
            background: #34495e;
            color: white;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
        }

        .contact-info {
            background: #ecf0f1;
            padding: 10px;
            border-radius: 6px;
            margin-top: 10px;
            font-size: 14px;
        }

        .private-badge {
            background: #e74c3c;
            color: white;
            padding: 4px 8px;
            border-radius: 12px;
            font-size: 10px;
            margin-left: 5px;
        }

        .public-badge {
            background: #27ae60;
            color: white;
            padding: 4px 8px;
            border-radius: 12px;
            font-size: 10px;
            margin-left: 5px;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- 관리자 토글 버튼 -->
        <button class="admin-toggle" onclick="toggleAdmin()">관리자</button>

        <!-- 관리자 패널 -->
        <div class="admin-panel" id="adminPanel">
            <div class="admin-login" id="adminLogin">
                <h3>관리자 로그인</h3>
                <input type="password" id="adminPassword" placeholder="관리자 비밀번호" style="margin: 20px 0; padding: 10px; border-radius: 8px; border: 1px solid #ddd;">
                <br>
                <button onclick="adminLogin()" style="background: #3498db; color: white; padding: 10px 20px; border: none; border-radius: 8px; cursor: pointer;">로그인</button>
            </div>
            
            <div class="admin-content" id="adminContent">
                <h3 style="color: #2c3e50; margin-bottom: 20px;">📋 관리자 패널</h3>
                
                <div class="admin-stats">
                    <div class="admin-stat-card">
                        <div style="font-size: 1.5em; font-weight: bold;" id="adminTotalCount">0</div>
                        <div>전체 건의사항</div>
                    </div>
                    <div class="admin-stat-card">
                        <div style="font-size: 1.5em; font-weight: bold;" id="adminPendingCount">0</div>
                        <div>승인 대기</div>
                    </div>
                    <div class="admin-stat-card">
                        <div style="font-size: 1.5em; font-weight: bold;" id="adminPublicCount">0</div>
                        <div>공개됨</div>
                    </div>
                </div>

                <h4 style="color: #2c3e50; margin-bottom: 15px;">모든 건의사항 관리</h4>
                <div id="adminSuggestionsList"></div>
            </div>
        </div>
        <!-- 헤더 -->
        <div class="header">
            <h1>부전연합역지구</h1>
            <h2>조합원 건의사항 및 질문</h2>
            <p>여러분의 소중한 의견을 남겨주세요.<br>좋은 의견 귀기울여 듣겠습니다.</p>
        </div>

        <!-- 메인 콘텐츠 -->
        <div class="main-content">
            <!-- 건의사항 입력 폼 -->
            <div class="suggestion-form">
                <h3 class="form-title">건의사항 / 질문 작성</h3>
                
                <form id="suggestionForm">
                    <div class="form-group">
                        <label for="name">성명</label>
                        <input type="text" id="name" name="name" placeholder="익명 접수 시 생략 가능">
                    </div>

                    <div class="form-group">
                        <label for="department">소속 부서/역</label>
                        <input type="text" id="department" name="department" placeholder="예: 부전역, 태화강역, 본부 등">
                    </div>

                    <div class="form-group">
                        <label for="contact">연락처</label>
                        <input type="tel" id="contact" name="contact" placeholder="010-0000-0000">
                    </div>

                    <div class="form-group">
                        <label for="category">분류 *</label>
                        <select id="category" name="category" required>
                            <option value="">선택해주세요</option>
                            <option value="근무환경">근무환경 개선</option>
                            <option value="복리후생">복리후생</option>
                            <option value="임금교섭">임금교섭 관련</option>
                            <option value="안전보건">안전보건</option>
                            <option value="교육훈련">교육훈련</option>
                            <option value="조합활동">조합활동</option>
                            <option value="인사">인사 관련</option>
                            <option value="기타">기타</option>
                        </select>
                    </div>

                    <div class="form-group">
                        <label for="title">제목 *</label>
                        <input type="text" id="title" name="title" required placeholder="건의사항 또는 질문의 제목을 입력해주세요">
                    </div>

                    <div class="form-group">
                        <label for="content">내용 *</label>
                        <textarea id="content" name="content" required placeholder="구체적인 건의사항이나 질문 내용을 자세히 작성해주세요"></textarea>
                    </div>

                    <div class="form-group">
                        <div class="anonymous-check">
                            <input type="checkbox" id="anonymous" name="anonymous">
                            <label for="anonymous">익명으로 접수</label>
                        </div>
                    </div>

                    <div class="form-group">
                        <div class="urgent-check">
                            <input type="checkbox" id="urgent" name="urgent">
                            <label for="urgent">⚠️ 긴급사안 (우선 처리 요청)</label>
                        </div>
                    </div>

                    <button type="submit" class="submit-btn">건의사항 접수하기</button>
                </form>
            </div>

            <!-- 접수된 건의사항 목록 -->
            <div class="suggestion-list">
                <h3 class="form-title">최근 접수된 건의사항</h3>
                <div id="suggestionsList">
                    <div style="text-align: center; color: #7f8c8d; padding: 40px;">아직 공개된 건의사항이 없습니다.</div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // 건의사항 데이터 저장소 (실제로는 서버 데이터베이스 연동 필요)
        let suggestions = [];

        // 관리자 기능
        let isAdminLoggedIn = false;
        const adminPassword = "940630"; // 실제 사용시 변경 필요

        function toggleAdmin() {
            const adminPanel = document.getElementById('adminPanel');
            if (adminPanel.style.display === 'none' || adminPanel.style.display === '') {
                adminPanel.style.display = 'block';
                if (isAdminLoggedIn) {
                    document.getElementById('adminLogin').style.display = 'none';
                    document.getElementById('adminContent').style.display = 'block';
                    updateAdminPanel();
                }
            } else {
                adminPanel.style.display = 'none';
            }
        }

        function adminLogin() {
            const password = document.getElementById('adminPassword').value;
            if (password === adminPassword) {
                isAdminLoggedIn = true;
                document.getElementById('adminLogin').style.display = 'none';
                document.getElementById('adminContent').style.display = 'block';
                updateAdminPanel();
                alert('관리자 로그인 성공!');
            } else {
                alert('비밀번호가 올바르지 않습니다.');
            }
        }

        function updateAdminPanel() {
            // 관리자 통계 업데이트
            const totalCount = suggestions.length;
            const pendingCount = suggestions.filter(s => !s.public).length;
            const publicCount = suggestions.filter(s => s.public).length;

            document.getElementById('adminTotalCount').textContent = totalCount;
            document.getElementById('adminPendingCount').textContent = pendingCount;
            document.getElementById('adminPublicCount').textContent = publicCount;

            // 모든 건의사항 목록 표시
            const adminList = document.getElementById('adminSuggestionsList');
            adminList.innerHTML = suggestions.map(suggestion => {
                const statusClass = `status-${suggestion.status}`;
                const statusText = {
                    'pending': '접수',
                    'reviewing': '검토중',
                    'processing': '진행중',
                    'completed': '완료'
                };

                return `
                    <div class="suggestion-manage">
                        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px;">
                            <div>
                                <span class="category-badge">${suggestion.category}</span>
                                <span class="date-badge">${suggestion.date}</span>
                                <span class="status-badge ${statusClass}">${statusText[suggestion.status]}</span>
                                ${suggestion.public ? '<span class="public-badge">공개</span>' : '<span class="private-badge">비공개</span>'}
                                ${suggestion.urgent ? '<span style="background: #e74c3c; color: white; padding: 4px 8px; border-radius: 12px; font-size: 10px;">긴급</span>' : ''}
                            </div>
                            <div style="font-size: 12px; color: #666;">#${suggestion.id}</div>
                        </div>
                        
                        <div style="font-weight: 600; margin-bottom: 8px;">${suggestion.title}</div>
                        <div style="color: #555; margin-bottom: 10px;">${suggestion.content}</div>
                        
                        <div class="contact-info">
                            <strong>작성자:</strong> ${suggestion.name} | 
                            <strong>소속:</strong> ${suggestion.department || '미입력'} | 
                            <strong>연락처:</strong> ${suggestion.contact || '미입력'}
                        </div>

                        <div class="suggestion-actions">
                            ${!suggestion.public ? `<button class="action-btn btn-approve" onclick="approveSuggestion(${suggestion.id})">공개 승인</button>` : ''}
                            ${suggestion.public ? `<button class="action-btn btn-reject" onclick="hideSuggestion(${suggestion.id})">공개 취소</button>` : ''}
                            <button class="action-btn btn-complete" onclick="completeSuggestion(${suggestion.id})">처리 완료</button>
                            <button class="action-btn btn-delete" onclick="deleteSuggestion(${suggestion.id})">삭제</button>
                        </div>
                    </div>
                `;
            }).join('');
        }

        function approveSuggestion(id) {
            const suggestion = suggestions.find(s => s.id === id);
            if (suggestion) {
                suggestion.public = true;
                suggestion.status = 'reviewing';
                updateSuggestionsList();
                updateStats();
                updateAdminPanel();
                alert('건의사항이 공개 승인되었습니다.');
            }
        }

        function hideSuggestion(id) {
            const suggestion = suggestions.find(s => s.id === id);
            if (suggestion) {
                suggestion.public = false;
                updateSuggestionsList();
                updateStats();
                updateAdminPanel();
                alert('건의사항이 비공개 처리되었습니다.');
            }
        }

        function completeSuggestion(id) {
            const suggestion = suggestions.find(s => s.id === id);
            if (suggestion) {
                suggestion.status = 'completed';
                updateSuggestionsList();
                updateStats();
                updateAdminPanel();
                alert('건의사항이 처리 완료되었습니다.');
            }
        }

        function deleteSuggestion(id) {
            if (confirm('정말로 이 건의사항을 삭제하시겠습니까?')) {
                const index = suggestions.findIndex(s => s.id === id);
                if (index !== -1) {
                    suggestions.splice(index, 1);
                    updateSuggestionsList();
                    updateStats();
                    updateAdminPanel();
                    alert('건의사항이 삭제되었습니다.');
                }
            }
        }
        document.getElementById('anonymous').addEventListener('change', function(e) {
            const nameField = document.getElementById('name');
            const contactField = document.getElementById('contact');
            
            if (e.target.checked) {
                nameField.value = '';
                nameField.placeholder = '익명 접수로 이름이 공개되지 않습니다';
                nameField.disabled = true;
                contactField.placeholder = '익명 접수 시 연락처는 총무부장만 확인 가능';
            } else {
                nameField.placeholder = '익명 접수 시 생략 가능';
                nameField.disabled = false;
                contactField.placeholder = '010-0000-0000';
            }
        });

        // 폼 제출 처리
        document.getElementById('suggestionForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const formData = new FormData(e.target);
            const suggestion = {
                id: suggestions.length + 1,
                name: formData.get('anonymous') ? '익명' : (formData.get('name') || '익명'),
                department: formData.get('department'),
                contact: formData.get('contact'),
                category: formData.get('category'),
                title: formData.get('title'),
                content: formData.get('content'),
                date: new Date().toISOString().split('T')[0],
                status: 'pending',
                anonymous: formData.get('anonymous') ? true : false,
                urgent: formData.get('urgent') ? true : false,
                public: false  // 새 건의사항은 기본적으로 비공개 (관리자 승인 필요)
            };id: suggestions.length + 1,
                name: formData.get('anonymous') ? '익명' : formData.get('name'),
                employeeId: formData.get('employee-id'),
                department: formData.get('department'),
                contact: formData.get('contact'),
                category: formData.get('category'),
                title: formData.get('title'),
                content: formData.get('content'),
                date: new Date().toISOString().split('T')[0],
                status: 'pending',
                anonymous: formData.get('anonymous') ? true : false,
                urgent: formData.get('urgent') ? true : false
            };

            suggestions.unshift(suggestion);
            
            // 폼 초기화
            e.target.reset();
            
            // 목록 업데이트
            updateSuggestionsList();
            updateStats();
            
            alert('건의사항이 성공적으로 접수되었습니다.\n접수번호: #' + suggestion.id + '\n\n※ 검토 후 적절한 건의사항은 공개 게시되며,\n빠른 시일 내에 답변드리겠습니다.');
        });

        // 건의사항 목록 업데이트 (공개된 것만 표시)
        function updateSuggestionsList() {
            const listContainer = document.getElementById('suggestionsList');
            const publicSuggestions = suggestions.filter(s => s.public === true);
            const recentSuggestions = publicSuggestions.slice(0, 5);
            
            if (recentSuggestions.length === 0) {
                listContainer.innerHTML = '<div style="text-align: center; color: #7f8c8d; padding: 40px;">아직 공개된 건의사항이 없습니다.</div>';
                return;
            }
            
            listContainer.innerHTML = recentSuggestions.map(suggestion => {
                const statusClass = `status-${suggestion.status}`;
                const statusText = {
                    'pending': '접수',
                    'reviewing': '검토중',
                    'processing': '진행중',
                    'completed': '완료'
                };
                
                return `
                    <div class="suggestion-item ${suggestion.urgent ? 'urgent' : ''}">
                        <div class="suggestion-header">
                            <span class="category-badge">${suggestion.category}</span>
                            <span class="date-badge">${suggestion.date}</span>
                            <span class="status-badge ${statusClass}">${statusText[suggestion.status]}</span>
                            ${suggestion.urgent ? '<span class="urgent-badge" style="background: #e74c3c; color: white; padding: 4px 8px; border-radius: 12px; font-size: 10px; margin-left: 5px;">긴급</span>' : ''}
                        </div>
                        <div class="suggestion-title">${suggestion.title}</div>
                        <div class="suggestion-content">${suggestion.content.substring(0, 100)}...</div>
                    </div>
                `;
            }).join('');
        }

        // 통계 업데이트 (공개된 건의사항만 집계)
        function updateStats() {
            const publicSuggestions = suggestions.filter(s => s.public === true);
            const stats = publicSuggestions.reduce((acc, suggestion) => {
                acc.total++;
                acc[suggestion.status]++;
                return acc;
            }, { total: 0, pending: 0, reviewing: 0, processing: 0, completed: 0 });

            document.getElementById('totalCount').textContent = stats.total;
            document.getElementById('pendingCount').textContent = stats.pending;
            document.getElementById('processingCount').textContent = stats.reviewing + stats.processing;
            document.getElementById('completedCount').textContent = stats.completed;
        }

        // 페이지 로드 시 초기화
        updateSuggestionsList();
        updateStats();
    </script>
</body>
</html>
