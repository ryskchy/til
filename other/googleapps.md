# Google Apps

## Google Drive API

### google drive apiのscope

* `https://www.googleapis.com/auth/drive.file` とすれば当該アプリで作成したファイルのみ読み書き可能

### mimetype

* google spreadsheetは'application/vnd.google-apps.spreadsheet'
* excel(xlsx)は'application/vnd.openxmlformats-officedocument.spreadsheetml.sheet'

### ファイルを上書きする場合

* `service.files().update(fileId='hogehoge', body=<file_metadata>, media_body=media).execute()`