# cloud-deployment-assignment

## 📌 Overview
This repository contains my practical assignment submission for [Enterprise Cloud Architecture]. It demonstrates how to set up a Spring Boot application connected to a MySQL database hosted on Google Cloud SQL.  

---

## 📹 Demo Video
Watch the demo here: [Google Drive Link](https://drive.google.com/file/d/1M6xkpR8u4OMtmn4tTuWmJOjolWFdiiao/view?usp=sharing)

> ⚡ Tip: Download the video for full HD quality if streaming appears blurry.

---

## 🛠️ How to Set Up MySQL Database in Google Cloud

### Step 1: Open Google Cloud Console
* Go to: [https://console.cloud.google.com/sql](https://console.cloud.google.com/sql)
* Make sure you’re in the right project.

---

### Step 2: Create Cloud SQL Instance
1. Click **Create Instance** → choose **MySQL**.  
2. Choose **MySQL 8.0** (recommended).  
3. Give it an **Instance ID** (e.g., `mysqldb`).  
4. Set the **root password** (e.g., `Mysql-ECA1!`).  
5. Region: pick **us-central1** (or closest to you).  
6. Availability: for testing, choose **Single zone**.

---

### Step 3: Enable Public IP for Testing
1. Go to your instance → **Connections** tab.  
2. Under **Public IP**, click **Add network**.  
3. Name it `local-testing`.  
4. For IP range, type `0.0.0.0/0` (⚠️ only for testing).  
5. Save and copy the **Public IP** (e.g., `34.135.121.174`).  

---

### Step 4: Create the Database Inside the Instance
1. Open Cloud Shell or your terminal and connect:

```bash
mysql -h <PUBLIC_IP> -P 3306 -u root -p
````

Example:

```bash
mysql -h 34.135.121.174 -P 3306 -u root -p
```

Enter your password (`Mysql-ECA1!`).

2. Inside MySQL shell, run:

```sql
CREATE DATABASE mysqldb;
```

3. Confirm creation:

```sql
SHOW DATABASES;
```

You should see `mysqldb`.

---

### Step 5: Connect Spring Boot Application

In `application-gcp.properties`:

```properties
spring.datasource.url=jdbc:mysql://34.135.121.174:3306/mysqldb?useSSL=false&allowPublicKeyRetrieval=true
spring.datasource.username=root
spring.datasource.password=Mysql-ECA1!
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

server.port=8081
```

Run your Spring Boot app. It will connect to your Cloud SQL database.

---

## 📂 Usage

1. Clone the repository:

```bash
git clone https://github.com/sasobapriyanjana11/cloud-deployment-assignment.git
```

2. Update `application-gcp.properties` with your database credentials if needed.

3. Run the Spring Boot application:

```bash
./mvnw spring-boot:run
```

4. Access the app at `http://localhost:8081`.

---

## 🔖 License

This project is open-source under the [MIT License](LICENSE).

---



