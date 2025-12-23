Declare PtrSafe Sub keybd_event Lib "user32" _
    (ByVal bVk As Byte, ByVal bScan As Byte, _
     ByVal dwFlags As Long, ByVal dwExtraInfo As Long)

Const VK_SCROLL As Byte = &H91

Sub StartOvernightRunKeepAwake()
    ToggleScrollLock
End Sub

Sub ToggleScrollLock()
    keybd_event VK_SCROLL, 0, 0, 0
    keybd_event VK_SCROLL, 0, 2, 0

    Application.OnTime Now + TimeValue("00:02:00"), "ToggleScrollLock"
End Sub

Sub StopKeepAwake()
    On Error Resume Next
    Application.OnTime Now + TimeValue("00:02:00"), "ToggleScrollLock", , False
End Sub
