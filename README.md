# การติดตั้งและรัน Supabase แบบ Self-Hosting

## ต้องติดตั้ง:

1. [Git](https://git-scm.com/downloads)
2. [Docker](https://docs.docker.com/engine/install/)
3. [Docker Compose](https://docs.docker.com/compose/install/)

---

## (1) การติดตั้ง Git

### Windows

- ดาวน์โหลด[ไฟล์ติดตั้งที่นี่](https://git-scm.com/downloads) และติดตั้งตามปกติ

### Linux: CentOS และ Amazon Linux 2

- รันคำสั่ง

```sh
yum install git -y
```

### Linux: Ubuntu

- รันคำสั่ง

```sh
apt-get install git
```

### macOS (ใช้ Homebrew)

- ถ้ายังไม่ติดตั้ง Homebrew ใช้คำสั่ง

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

- เมื่อติดตั้ง Homebrew แล้ว, รันคำสั่ง

```sh
brew install git
```

---

## (2) การติดตั้ง Docker

### Windows

- ติดตั้งตามขั้นตอนนี้ [Install Docker Desktop on Windows](https://docs.docker.com/desktop/install/windows-install/)

### Linux: CentOS และ Amazon Linux 2

1. ให้รันคำสั่งนี้เพื่อเข้าใช้งานสิทธิ์ root และ update server ให้เป็นปัจจุบัน

```bash
sudo su -
yum update -y
```

2. ทำการติดตั้ง docker

```bash
yum install -y docker
```

3. ทำการ start docker

```bash
systemctl start docker
```

4. ทำการตั้งค่า user (ตัวอย่างคำสั่งของ Amazon Linux 2)

```bash
usermod -a -G docker ec2-user
```

5. ทำการเปิดใช้งาน docker

```bash
systemctl enable docker
```

6. ทำการตรวจสอบ version

```bash
docker --version
```

### Linux: Ubuntu (22.04 LTS)

- ติดตั้งตามขั้นตอนของ
  DigitalOcean: [How To Install and Use Docker on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04)

### macOS

- ติดตั้งตามขั้นตอนนี้ [Install Docker Desktop on Mac](https://docs.docker.com/desktop/install/mac-install/)

---

## (3) การติดตั้ง docker-compose

### Windows

- จะถูกติดตั้งพร้อม Docker Desktop แล้ว

### Linux: Ubuntu, CentOS และ Amazon Linux 2

- ดู link ดาวน์โหลดเวอร์ชันล่าสุดจาก [Install the Compose standalone](https://docs.docker.com/compose/install/other/)

1. รันคำสั่ง

```sh
curl -SL https://github.com/docker/compose/releases/download/v2.16.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
```

2. ทำการ change mode เพื่อให้สามารถ execute ไฟล์ได้

```bash
chmod +x /usr/local/bin/docker-compose
```

3. ทำการอนุญาตสิทธิ์ให้กับ docker.sock

```bash
chmod 666 /var/run/docker.sock
```

4. ทำการตรวจสอบ version อีกครั้ง

```bash
docker-compose --version
```

---

## (4) ติดตั้งและรัน Supabase แบบ Self-Hosting

1. ดาวน์โหลด Supabase

```sh
git clone --depth 1 https://github.com/supabase/supabase
```

2. เข้าไปใน docker folder

```sh
cd supabase/docker
```

3. copy ตัวอย่าง .env (อย่านำไปใช้จริงบน production)

```sh
cp .env.example .env
```

4. รัน Supabase ด้วยคำสั่ง

```sh
docker-compose up
```

5. เข้าไปใช้งาน Supabase ที่ http://localhost:3000

---

## (เพิ่มเติม) เพิ่มความปลอดภัยให้กับการติดตั้ง

- ถ้าต้องการทดสอบใช้งาน ไม่ต้องทำก็ได้ แต่หากต้องการใช้งานบน production จำเป็นต้องทำ
- ทำตามขั้นตอนในเอกสารของ Supabase: https://supabase.com/docs/guides/self-hosting/docker