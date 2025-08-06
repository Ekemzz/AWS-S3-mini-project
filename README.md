# AWS-S3-mini-project
Sure! Here's a **brief and clear summary of AWS S3**:

---

## 🪣 **What is AWS S3?**

**Amazon S3 (Simple Storage Service)** is a **scalable object storage service** that lets you store and retrieve any amount of data — anytime, from anywhere on the web.

It’s designed for **durability, security, and high availability**, making it ideal for storing:

* Images, videos, documents
* Backups and logs
* Static website files
* Big data and analytics files

---

## 🔑 Key Concepts

| Term       | Meaning                                                 |
| ---------- | ------------------------------------------------------- |
| **Bucket** | A container for storing objects (like a folder)         |
| **Object** | A file + its metadata (e.g., a photo or document)       |
| **Key**    | The unique name of an object inside a bucket            |
| **Region** | The geographic location where your bucket and data live |

---

## 🔐 Features

* **Highly durable** (99.999999999% or "11 nines")
* **Versioning** to keep multiple copies of a file
* **Encryption** for data security
* **Access control** using IAM policies, ACLs, or bucket policies
* **Event notifications** (e.g., trigger a Lambda function when a file is uploaded)

---

## 🧠 Example Use Case

* Hosting a **static website** (HTML, CSS, JS)
* Storing **profile pictures** for a mobile app
* Archiving **log files** or backups

---

## 🧪 Basic Commands (AWS CLI)

```bash
# Create a bucket
aws s3 mb s3://my-new-bucket

# Upload a file
aws s3 cp file.txt s3://my-new-bucket/

# List objects
aws s3 ls s3://my-new-bucket/

# Download a file
aws s3 cp s3://my-new-bucket/file.txt .
```


---

## ✅ **Benefits of Amazon S3**

| Benefit                | Description                                                                      |
| ---------------------- | -------------------------------------------------------------------------------- |
| **Scalable**           | Stores unlimited data — from kilobytes to petabytes                              |
| **Durable**            | 99.999999999% (11 nines) durability ensures your files are safe                  |
| **Secure**             | Supports encryption (server-side & client-side), IAM policies, bucket policies   |
| **Cost-effective**     | Pay only for what you use, with tiered storage classes (e.g., Standard, Glacier) |
| **Easy to use**        | Simple web interface, CLI, SDKs, and REST API                                    |
| **Reliable**           | Highly available across multiple data centers (availability zones)               |
| **Fast access**        | Delivers data globally via S3 + CloudFront integration                           |
| **Event-driven**       | Can trigger AWS Lambda or SNS when files are uploaded or modified                |
| **Backup and restore** | Supports versioning and cross-region replication                                 |

---

## 📦 **Common Use Cases for Amazon S3**

### 1. **Static Website Hosting**

Host HTML/CSS/JS websites without needing a server.

> Example: A portfolio, landing page, or company website.

---

### 2. **Application Data Storage**

Store images, videos, user uploads, and logs used by web/mobile apps.

> Example: Profile pictures for users in a social media app.

---

### 3. **Backup and Restore**

Use S3 to back up data from EC2, databases, or on-premise systems.

> Example: Automatic backup of logs or production databases.

---

### 4. **Big Data Analytics**

Store and analyze massive datasets with services like Athena, Redshift, or EMR.

> Example: Store IoT sensor data or web traffic logs for querying.

---

### 5. **Disaster Recovery**

Use S3 with cross-region replication to maintain a reliable DR plan.

> Example: Replicating important files from one AWS region to another.

---

### 6. **Media Hosting and Streaming**

Store and serve videos, podcasts, or music files efficiently.

> Example: An e-learning platform serving recorded lessons.

---

### 7. **Data Lake Storage**

Centralized repository for structured and unstructured data.

> Example: Companies aggregating sales, customer, and product data in S3.

---

### 8. **Software Delivery**

Host downloadable files, software packages, or app updates.

> Example: Delivering app installers to users globally.

---

## 🧠 Summary

> **Amazon S3 is a powerful, reliable, and flexible object storage service** used for everything from website hosting to big data analysis, with the ability to scale, secure, and serve data efficiently.
**S3 is AWS’s object storage service** that is flexible, secure, and ideal for storing files of any kind — from app data to backup files to website content.




---

## 🔁 **What is S3 Versioning?**

**S3 Versioning** is a feature that lets you **preserve, retrieve, and restore** **every version of every object** in a bucket.

When enabled, every time you upload or modify a file with the same key (name), **S3 stores a new version** — the old one is **not deleted**.

---

## 🧠 Why Use Versioning?

| Purpose                            | Benefit                                     |
| ---------------------------------- | ------------------------------------------- |
| **Accidental deletion protection** | Restore deleted or overwritten files easily |
| **Audit trail**                    | Track changes over time                     |
| **Backup & recovery**              | Keep historical versions of critical data   |
| **Data integrity**                 | Undo user errors or corruption              |

---

## 🔧 How to Enable Versioning

You can enable versioning **when creating a bucket** or on an **existing bucket**.

### ✅ Using the AWS CLI:

```bash
aws s3api put-bucket-versioning \
    --bucket my-bucket-name \
    --versioning-configuration Status=Enabled
```

### ✅ Using the AWS Console:

1. Go to **S3 > Your Bucket**
2. Click **Properties**
3. Scroll to **Bucket Versioning**
4. Click **Edit > Enable > Save changes**

---

## 🔍 What Happens When Versioning is Enabled?

* Uploading a file again → **adds a new version**, doesn't replace the old one.
* Deleting a file → **adds a delete marker**, but older versions remain.

---

### 🧪 Example:

1. You upload `report.pdf`
2. You upload a new `report.pdf` — S3 keeps **both versions**
3. You delete `report.pdf` — S3 adds a **delete marker**, but you can still access earlier versions

---

## 🛠 How to Work with Versions (CLI)

* **List all versions:**

```bash
aws s3api list-object-versions --bucket my-bucket-name
```

* **Download a specific version:**

```bash
aws s3api get-object --bucket my-bucket-name --key file.txt --version-id abc123xyz456 ./file.txt
```

* **Delete a specific version:**

```bash
aws s3api delete-object --bucket my-bucket-name --key file.txt --version-id abc123xyz456
```

---

## ⚠️ Important Notes

* **Versioning cannot be fully disabled** once enabled — you can only *suspend* it.
* It may **increase storage costs**, since every version is stored.
* To permanently delete a file, you must **remove all versions**, including the delete marker.

---

## 🧾 Summary

> **S3 Versioning lets you preserve, track, and recover every version of your objects.** It's essential for data protection, especially in environments where accidental deletion or overwrites can happen.

---
S3 PROJECT
1. Navigate the console page and search for s3.

<img width="959" height="475" alt="image" src="https://github.com/user-attachments/assets/202a74e6-8e50-45de-a612-d4be024bec2f" />

2. Locate and create a bucket.

<img width="953" height="459" alt="image" src="https://github.com/user-attachments/assets/25a85ce3-27af-416f-824c-2b4d05cc6936" />

3. After clicking on "create bucket", disable ACLs, block all public access, disbale versioning and proceed with default settings.

<img width="956" height="469" alt="image" src="https://github.com/user-attachments/assets/bd30a08a-2610-4bac-af3b-55a6ddf7d2a8" />
<img width="945" height="470" alt="image" src="https://github.com/user-attachments/assets/5f2f9848-14cb-4af2-964f-cb53ee40d039" />
<img width="953" height="448" alt="image" src="https://github.com/user-attachments/assets/32c22027-534a-4e9f-9efe-c7131efcfeab" />
<img width="938" height="424" alt="image" src="https://github.com/user-attachments/assets/b2ce4df4-d0ef-4496-a2df-862b01d4816e" />
<img width="953" height="480" alt="image" src="https://github.com/user-attachments/assets/6278e11f-cfe7-4453-9024-0d5541ae891f" />

3a. Changed the name of the bucket from my-first-s3-bucket to my-first-s3-bucket-009
<img width="959" height="478" alt="image" src="https://github.com/user-attachments/assets/347f2738-2915-449f-906d-5db208911cb5" />

4. Text document that will serve as an object for the bucket

  <img width="959" height="500" alt="image" src="https://github.com/user-attachments/assets/7320965d-488e-4c90-b3d6-51b841a09099" />

5. Click upload and subsequently add file. Choose the "Hello welcome" file and open

<img width="944" height="437" alt="image" src="https://github.com/user-attachments/assets/cbde01b6-6ec8-4fc1-a7b6-fe7fce82f7ad" />
<img width="952" height="437" alt="image" src="https://github.com/user-attachments/assets/2f595b65-4737-4411-8fc9-578bcc59420d" />
<img width="952" height="470" alt="image" src="https://github.com/user-attachments/assets/c4ab78c2-80e2-40f2-bdf9-6b350518f27a" />

6. Confirm that file has been added and then upload.

<img width="953" height="444" alt="image" src="https://github.com/user-attachments/assets/df051af3-51de-49a9-ae7d-b9aa7fe94499" />
<img width="932" height="419" alt="image" src="https://github.com/user-attachments/assets/6ff05fbb-7fd0-4158-a202-0815458db0bc" />
<img width="931" height="436" alt="image" src="https://github.com/user-attachments/assets/3da8ce3b-b387-4d55-a69c-ed56dfef5a2f" />


7. Enabling versioning
   
   7a. Navigate to the properties of the bucket and confirm that versioning is disabled
   <img width="947" height="436" alt="image" src="https://github.com/user-attachments/assets/525d9b94-2ca1-4e42-8a39-fd41f4b6a997" />
   

   7b. click edit and enable versioning
  <img width="953" height="469" alt="image" src="https://github.com/user-attachments/assets/fe79b3fb-59c9-42f7-b3b2-d590a44dbd31" />
  <img width="937" height="421" alt="image" src="https://github.com/user-attachments/assets/4cb5ad30-a339-4ef4-8fc9-9e88fb300c02" />


   7c. Edit the "Hello welcome" file and add it to the bucket
   <img width="948" height="496" alt="image" src="https://github.com/user-attachments/assets/6929df12-4820-4bc8-a972-e14123327d79" />

   7d. Toggle the show versions to reveal the versions of the file added
   <img width="934" height="434" alt="image" src="https://github.com/user-attachments/assets/1d30a6de-dbe9-4cc0-8643-07ae5185f74a" />

8. To view content of versions
   8a. Go to permissions and edit public access to unblock. Afterwards, save changes. Enusre to type in "confirm" to allow for changes implementation.
   <img width="950" height="445" alt="image" src="https://github.com/user-attachments/assets/5fb6f026-d154-47dd-a936-b661a2725bcf" />
   <img width="948" height="428" alt="image" src="https://github.com/user-attachments/assets/cfba4a3f-cb58-4be3-b7a6-afb0e38076e9" />
   <img width="940" height="424" alt="image" src="https://github.com/user-attachments/assets/f0002885-d9b0-4918-b2e9-1f4c96ad3a54" />


  8b. Notice the caution on the public access. Now, create a policy for what actions the public are allowed to take on.
  <img width="922" height="374" alt="image" src="https://github.com/user-attachments/assets/a0bd455f-d9f3-4d8b-a4f2-5acc7e37e1ef" />
  Still on permission section, navigate to bucket policy and click edit.
  <img width="946" height="436" alt="image" src="https://github.com/user-attachments/assets/49eece4d-019b-4af5-b586-aeb22c29b16e" />
  See the bucket ARN and the policy generator. click on the generator and edit the desired policy.
  <img width="959" height="433" alt="image" src="https://github.com/user-attachments/assets/08a19fa7-c30f-4c11-8196-e0f5957655a5" />

<img width="935" height="400" alt="image" src="https://github.com/user-attachments/assets/602abd8a-a426-4c65-939b-2741695d1732" />
<img width="935" height="457" alt="image" src="https://github.com/user-attachments/assets/426106da-c642-4e58-ac00-c0cdb8c70b52" />
Click on add statement and generate policy.
<img width="931" height="425" alt="image" src="https://github.com/user-attachments/assets/93bfcaf8-f5df-44d9-83dd-2d542013344c" />
Copy the json policy generated and paste it at the policy field and save it.
<img width="950" height="489" alt="image" src="https://github.com/user-attachments/assets/64cc7873-d8db-41ff-b39b-5bb18b83972e" />
<img width="935" height="422" alt="image" src="https://github.com/user-attachments/assets/eefa1e58-089f-4931-89f2-759b977047cc" />


9. Now, lets view the contents. The persimmions are well set alongside the policy.
    <img width="938" height="449" alt="image" src="https://github.com/user-attachments/assets/7dea4b82-d6f6-4d49-bdf3-ecb476c1c217" />
    <img width="946" height="422" alt="image" src="https://github.com/user-attachments/assets/35bcab67-351e-4b69-aaa6-13c306cbc321" />

    Copy the url and see the contents. view both versions
   <img width="957" height="475" alt="image" src="https://github.com/user-attachments/assets/26069bc7-213c-4d93-918a-917e0a61ff82" />
   <img width="959" height="485" alt="image" src="https://github.com/user-attachments/assets/5e2c65eb-78df-4438-ba4f-6b7d59af1a5e" />

10. Craeting lifecycles
    10a. Naviagte to tyhe management section and click create lifecycle
   <img width="959" height="451" alt="image" src="https://github.com/user-attachments/assets/ae3ed6ee-d342-41d3-87e5-a28e1f2b8dbe" />
  <img width="957" height="450" alt="image" src="https://github.com/user-attachments/assets/ba4d8b7d-802b-4c70-a9dc-6d5969d16c90" />
  <img width="957" height="466" alt="image" src="https://github.com/user-attachments/assets/69d7a9af-8b6b-487b-a319-c2af3dff24bc" />
    After stating the lifecycle name, object min and max size, transition plan on storage classes, you save changes
<img width="932" height="410" alt="image" src="https://github.com/user-attachments/assets/81507f86-833c-49bf-a3ba-6cf17b027bbf" />

    <img width="935" height="416" alt="image" src="https://github.com/user-attachments/assets/4559fea6-8098-4518-aa1e-a9087e82a59e" />








