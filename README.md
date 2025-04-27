# Django CVE-2021-35042 PoC 보고서

## 개요

- **CVE 번호**: CVE-2021-35042
- **취약점 설명**: Django의 ORM(QuerySet)에서 `order_by()` 메소드가 사용자 입력을 적절히 검증하지 않고 처리하여 **SQL Injection** 취약점이 발생할 수 있음.
- **영향 버전**: Django 2.2 ~ 2.2.24, 3.1 ~ 3.1.12, 3.2 ~ 3.2.4
- **공식 패치**: Django 2.2.25, 3.1.13, 3.2.5 버전에서 수정됨
- **참고 링크**: [Django 공식 보안 공지](https://www.djangoproject.com/weblog/2021/jul/01/security-releases/)

---

## 환경 구성

- **OS**: Ubuntu 20.04 (Docker container)
- **Docker**: Docker version 24.0.5
- **Django 버전**: 3.2.4 (취약한 버전)
- **Database**: SQLite (테스트 목적)

---

## Dockerfile

```Dockerfile
FROM python:3.8-slim

RUN pip install django==3.2.4

WORKDIR /app

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
