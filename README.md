# task-bash-script
Bash script for daily backups".
SOURCE_DIR → الفولدر اللي هيتعمله Backup (هنا /etc).

BACKUP_DIR → المكان اللي النسخ الاحتياطية هتتحفظ فيه (/opt/backups/system).

LOG_DIR → مكان تخزين ملفات اللوج (/var/log/system-backup).

RETENTION_DAYS → عدد الأيام اللي النسخ هتتخزن قبل ما تتشال (هنا 7 أيام).

LOG_RETENTION → عدد ملفات اللوج اللي هتحتفظ بيها (هنا 5).

EMAIL_TO → الإيميل اللي هيجيله تنبيه لو الباك أب فشل.

HOSTNAME → بياخد اسم الجهاز.



2. بيعمل الفولدرات اللي هيخزن فيها الباك أب واللوج لو مش موجودة (mkdir -p).


3. بيحدد التاريخ والوقت ويحطهم في اسم ملف الباك أب واسم ملف اللوج.
#!/bin/bash

# 1. تحديد مسار الملفات اللي هنعمل لها Backup
SOURCE_DIR="/var/www/html"

# 2. تحديد مكان حفظ النسخة
BACKUP_DIR="/home/user/backups"

# 3. اسم ملف النسخة فيه التاريخ والوقت
DATE=$(date +'%Y-%m-%d_%H-%M-%S')
BACKUP_FILE="backup_$DATE.tar.gz"

# 4. إنشاء النسخة الاحتياطية
tar -czf "$BACKUP_DIR/$BACKUP_FILE" "$SOURCE_DIR"

# 5. طباعة رسالة نجاح
echo "Backup created successfully: $BACKUP_DIR/$BACKUP_FILE"
