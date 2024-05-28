# minhlaiii
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trang web cá nhân</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f5f5f5;
            color: #333;
        }

        header {
            background-color: #333;
            color: #fff;
            padding: 20px;
            text-align: center;
        }

        nav ul {
            list-style-type: none;
            margin: 0;
            padding: 0;
        }

        nav ul li {
            display: inline;
            margin-right: 20px;
        }

        nav ul li a {
            color: #fff;
            text-decoration: none;
        }

        main {
            padding: 20px;
        }

        section {
            margin-bottom: 20px;
        }

        footer {
            background-color: #333;
            color: #fff;
            text-align: center;
            padding: 10px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Trang cá nhân của [Tên của bạn]</h1>
        <nav>
            <ul>
                <li><a href="#home">Trang chủ</a></li>
                <li><a href="#projects">Dự án cá nhân</a></li>
                <li><a href="#blog">Blog</a></li>
                <li><a href="#schedule">Lịch trình</a></li>
                <li><a href="#upload">Tải lên file Word</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section id="home">
            <h2>Trang chủ</h2>
            <!-- Phần hiển thị dự án cá nhân và bài đăng blog -->
        </section>

        <section id="projects">
            <h2>Dự án cá nhân</h2>
            <!-- Chi tiết các dự án cá nhân -->
        </section>

        <section id="blog">
            <h2>Blog</h2>
            <!-- Các bài đăng trên blog -->
        </section>

        <section id="schedule">
            <h2>Lịch trình</h2>
            <!-- Lịch trình công việc hoặc sự kiện -->
        </section>

        <section id="upload">
            <h2>Tải lên file Word</h2>
            <!-- Form để tải lên file Word -->
            <form id="uploadForm">
                <input type="file" id="fileInput" accept=".doc, .docx">
                <button type="submit">Tải Lên</button>
            </form>
            <div id="message"></div>
        </section>
    </main>

    <footer>
        <p>&copy; 2024 Trang cá nhân của [Tên của bạn]</p>
    </footer>

    <script>
        const form = document.getElementById('uploadForm');
        const fileInput = document.getElementById('fileInput');
        const message = document.getElementById('message');

        form.addEventListener('submit', async (event) => {
            event.preventDefault();

            const file = fileInput.files[0];
            if (!file) {
                message.textContent = 'Vui lòng chọn một file để tải lên.';
                return;
            }

            const formData = new FormData();
            formData.append('file', file);

            try {
                const response = await fetch('upload.php', {
                    method: 'POST',
                    body: formData
                });

                if (response.ok) {
                    message.textContent = 'File đã được tải lên thành công.';
                } else {
                    message.textContent = 'Đã xảy ra lỗi khi tải lên file.';
                }
            } catch (error) {
                console.error('Lỗi:', error);
                message.textContent = 'Đã xảy ra lỗi khi tải lên file.';
            }
        });
    </script>
</body>
</html>
