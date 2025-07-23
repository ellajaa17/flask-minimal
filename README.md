# flask-minimal

A minimal Flask starter project designed to help you quickly set up a clean, simple, and efficient web application. This project is structured to keep things lightweight and focuses on productivity, with all your code contained in a single file (`app.py`), along with basic templates and static assets.


## Features
- Single-file Flask application (`app.py`) to maximize productivity and simplicity.
- Basic HTML template structure with minimal styling and JavaScript.
- Simple and intuitive project setup with no unnecessary complexity.
- Easily customizable for rapid development of web applications.

## Preparation
```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip -y
```

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/flask-minimal.git
   cd flask-minimal
   ```

2. Create a virtual environment (recommended):
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Run the app:
   ```bash
   python app.py
   ```

The Flask app will start, and you can view it by navigating to http://localhost:5000 in your browser.

##TAMBAHAN

Agar Flask-app otomatis berjalan setiap kali EC2 instance dinyalakan kita bisa menggunakan systemd, caranya :
1. Buat file service untuk systemd

```bash
sudo nano /etc/systemd/system/flask-app.service
```
Paste isi file service, sesuaikan path jika berbeda.
```
 [Unit]
Description=Flask Minimal App
After=network.target

[Service]
Type=simple
User=ubuntu
WorkingDirectory=/home/ubuntu/flask-minimal
Environment=PATH=/home/ubuntu/flask-minimal/venv/bin
ExecStart=/home/ubuntu/flask-minimal/venv/bin/python app.py
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

Aktifkan dan jalankan service

```bash
# Reload systemd
sudo systemctl daemon-reload

# Enable service (akan start otomatis saat boot)
sudo systemctl enable flask-app.service

# Start service sekarang
sudo systemctl start flask-app.service

# Cek status
sudo systemctl status flask-app.service
```

## Penggunaan

Proyek starter ini siap digunakan sebagai fondasi untuk membangun aplikasi web. File app.py berisi semua rute dan logika Flask, membuatnya mudah untuk diperluas dan disesuaikan. Anda dapat menambahkan lebih banyak template, rute, atau file statis sesuai kebutuhan.

## Kostumisasi
You can easily modify:

 - Struktur HTML di `templates/index.html`
 - Styling di `static/style.css`
 - Interaktivitas di `static/script.js`

Jangan ragu untuk memperbarui file app.py untuk menambahkan rute atau logika tambahan sesuai kebutuhan Anda.

## Usage

This starter project is ready to be used as a foundation for building web applications. The app.py file contains all the Flask routes and logic, making it simple to expand and customize. You can add more templates, routes, or static files as needed.

## Customization
You can easily modify:

 - The HTML structure in `templates/index.html`
 - The styling in `static/style.css`
 - The interactivity in `static/script.js`

Feel free to update the app.py file to add your routes or any additional logic to fit your needs.

## License
This project is licensed under the MIT License.

## Contributing
Feel free to fork this repository and create pull requests if you have improvements or bug fixes. If you have any suggestions, open an issue, and we’ll discuss it!

This project is built with simplicity and efficiency in mind, perfect for quickly starting small web apps or prototypes with minimal overhead.
