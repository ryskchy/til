## dllを別フォルダにまとめる
* app.config内、`<probing privatePath="lib" />`と足すとlib内に入る

```
<runtime>
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
 <probing privatePath="lib" />
</assemblyBinding>
</runtime>
```