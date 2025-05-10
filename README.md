## 🚀 DevOps CI/CD Pipeline

This project demonstrates a simple **CI/CD pipeline** that automatically pulls and deploys changes from a GitHub repository using **Python**, **Shell scripting**, and **cron jobs**, with `nginx` serving a static `index.html` page.

---

## 📁 Project Structure

```
CI-CD_Pipeline_Tool/
│-- python&shellScripting/
│   ├── check_commits.py     # Script to check for new commits
│   ├── deploy.sh            # Deployment script
│-- .gitignore               # Git ignore file
│-- index.html               # Sample index page
│-- README.md                # Project documentation
```
---

## ✨ Features

- 🔁 **Automated Commit Checking** via `check_commits.py`
- 🚚 **Auto Deployment** using `deploy.sh`
- ⏱️ **Cron Job Integration** for periodic execution
- 🌐 **Nginx Setup** to serve static content
- 🔐 **Token-Based GitHub Authentication**
- 📄 **Execution Logging** for audit and debugging

---

## 🧰 System Requirements

Ensure the following are installed on your Ubuntu/Linux system:

```bash
sudo apt update
sudo apt install -y nginx git python3 pipx
pipx ensurepath
```
---

## ⚙️ Project Setup

1. Set up your Github Token with GitHub.
2. Clone the repository:
   ```bash
   cd /var/www/html/
   git clone <your_repo_url>
   ```
3. Create a `log` directory:
   ```bash
   mkdir log && chmod 755 log
   ```

4. Copy the provided scripts:
   - `check_commits.py`
   - `deploy.sh`  
   (Refer to `deploy_sample/`)

5. Make both scripts executable:
   ```bash
   chmod 755 check_commits.py deploy.sh
   ```
---

## 🔐 GitHub Token Setup

### On Ubuntu:
1. Install `python3-dotenv`:
   ```bash
   sudo apt install -y python3-dotenv
   ```
2. Create a `.env` file and add your GitHub token:
   ```python
   GITHUB_TOKEN = "your_github_token"
   ```
3. ✅ Make sure .env is listed in .gitignore.

### On Windows:
1. Install dotenv:
   ```bash
   pip install python-dotenv
   ```
2. Create a `.env` file and add your GitHub token:
   ```python
   GITHUB_TOKEN = "your_github_token"
   ```
3. Ensure `.env` is listed in `.gitignore`.
---

## 🌍 Nginx Setup

1. Update Nginx configuration:

```bash
sudo nano /etc/nginx/sites-available/default
```

2. Set the root to:

```nginx
root var/www/html/Devops_pipeline/;
```


## ⏰ Cron Job Setup (Every 5 Minutes)

1. Edit crontab:

```bash
crontab -e
```


2. Add the following line (adjust paths as needed):

```cron
*/5 * * * * /usr/bin/python3 /var/www/html/check_commits.py >> /var/www/html/log/check_commits.log 2>&1
```

4. Validate Cron:

```bash
crontab -l
systemctl status cron
```
---

## 🖼️ Validation Snapshots
1. Project Repo directories and files:<br>
<img  src="https://github.com/praysap/Devops_pipeline/blob/main/Screenshot/project.png" /><br>

2. Github token setup in .env file:<br>
<img  src="https://github.com/praysap/Devops_pipeline/blob/main/Screenshot/directory.png" /><br>

3. Nginx setup:<br>
<img  alt="image" src="https://github.com/praysap/Devops_pipeline/blob/main/Screenshot/server_nginx.png" /><br>

4. Crontab setup:<br>
<img  alt="image" src="https://github.com/praysap/Devops_pipeline/blob/main/Screenshot/crontab.png" /><br>

5. Log directory files:<br>
<img  alt="image" src="https://github.com/praysap/Devops_pipeline/blob/main/Screenshot/logs.png" /><br>

6. Latest Commit details storing in a file (latest_commit.txt):<br>
<img  src="https://github.com/praysap/Devops_pipeline/blob/main/Screenshot/commit.png" /><br>

7. Deployment logs storing in a file (deploy.log):<br>
<img  src="https://github.com/praysap/Devops_pipeline/blob/main/Screenshot/deploy_logs_file.png" /><br>

8. Checking commits to do the latest deployment on the server (checking_commits.log):<br>
<img  src="https://github.com/praysap/Devops_pipeline/blob/main/Screenshot/Check_New_commit.png" /><br>


9. Commit History
<img  src="https://github.com/praysap/Devops_pipeline/blob/main/Screenshot/Commit_histroy.png" /><br>

10. CI/CD Pipeline Final Output:
<img  src="https://github.com/praysap/Devops_pipeline/blob/main/Screenshot/output_Final.png" /><br>
---

🙌 Contribution
Feel free to raise issues or submit pull requests to improve the project. Contributions are always welcome!

