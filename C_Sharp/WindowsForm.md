## FormのOK, Cancel
* Form.AcceptButton, Form.CancelButtonにボタンを設定しておくと、そのフォームのOKボタン、Cancelボタンとして認識される
  * フォームを選択した状態でEnterキーを押すとForm.AcceptButtonが押され、Form.DialogResult にOK が設定された状態でフォームが閉じる
  * Escキーを押すとForm.CancelButtonが押され、Form.DialogResultにCancelが設定された状態でフォームを閉じる
  * DialogResultはクリックイベントより先に設定される
  * DialogResultが設定されると、クリックイベント実行後にフォームが閉じる
    * OKボタン、Cancelボタン内でフォームを閉じずに関数を抜けるときは、クリックイベント内でForm.DialogResultにDialogResult.Noneを設定する

## DataError