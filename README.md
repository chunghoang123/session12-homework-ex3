# Session 12 - Ex3: CD da moi truong Staging & Production

## Muc tieu
Dung GitHub Environments de tach staging/production, bat Required reviewers cho production.

## Buoc 1: Tao Environments tren GitHub
1. Vao repo -> **Settings -> Environments -> New environment**: tao `staging`.
2. Tao tiep `production`.
3. Vao `production` -> tick **Required reviewers** -> chon tai khoan ca nhan -> Save.
4. (Tuy chon) dat `Environment URL`: staging `https://api.staging.example.com`, production `https://api.prod.example.com`.

## Buoc 2: Workflow `.github/workflows/cd-multi-env.yml`
- Trigger: push vao `develop` va `main`.
- Job `deploy-staging` co `environment: staging`, chi chay khi `refs/heads/develop`.
- Job `deploy-prod` co `environment: production`, chi chay khi `refs/heads/main` -> se dung o trang thai **Waiting for review** cho den khi Approve.

## Kiem tra
1. Push vao `develop`: thay `deploy-staging` chay xanh ngay, `deploy-prod` bi skip.
2. Push vao `main`: thay `deploy-prod` hien **Waiting for review** (mau vang), bam **Review deployments -> Approve and deploy** thi moi chay tiep.
3. Chup man hinh cua so phe duyet de nop bai.

## Chay local
```bash
./gradlew test
```
