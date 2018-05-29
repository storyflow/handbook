# 数据合并

## 相关代码

```
Sub 工作薄间工作表合并()   
Dim FileOpen
Dim X As Integer
Application.ScreenUpdating = False
FileOpen = Application.GetOpenFilename(FileFilter:="Microsoft Excel文件(*.xlsx),*.xlsx", MultiSelect:=True, Title:="合并工作薄")
X = 1
While X <= UBound(FileOpen)
Workbooks.Open Filename:=FileOpen(X)
Sheets().Move After:=ThisWorkbook.Sheets(ThisWorkbook.Sheets.Count)
X = X + 1
Wend
ExitHandler:
Application.ScreenUpdating = True
End Sub
```

```
Sub 合并当前工作簿下的所有工作表()
Application.ScreenUpdating = False
For j = 1 To Sheets.Count
    If Sheets(j).Name <> ActiveSheet.Name Then
       X = Range("A65536").End(xlUp).Row + 1
       Sheets(j).UsedRange.Copy Cells(X, 1)
   End If
Next
Range("B1").Select
Application.ScreenUpdating = True
MsgBox "当前工作簿下的全部工作表已经合并完毕！", vbInformation, "提示"
End Sub
```

## 参考资料
* [如何将多个Excel工作簿合并成一个新工作簿？](http://www.zhangzhengxiong.com/?id=94)