
## Ubuntu 22.04.2 LTS

```bash
sudo systemctl reboot --firmware-setup
```

用來重新啟動系統並進入固件設置模式（也稱為 BIOS 或 UEFI 設置模式）的命令。

它由以下三部分組成：

- `sudo`：這個關鍵字表示需要使用超級用戶權限運行命令。請注意，在運行這個命令之前，系統會要求您輸入您的密碼。

- `systemctl reboot`：這部分命令用來重新啟動系統。它會將系統關閉，然後重新啟動系統。

  - `systemctl` 是一個用於管理 `Systemd` 系統和服務的命令行工具。`Systemd` 是一個用於管理 Linux 系統的系統和服務的守護進程，它負責管理系統的各種組件和進程，例如初始化進程、網絡服務、日誌記錄、進程控制等。

  `systemctl` 命令可以用來**啟動、停止、重啟和查詢系統中運行的 Systemd 服務**。使用 systemctl 命令還可以查看服務的運行狀態、啟動時間、最後一次啟動的結果等詳細信息。在 Linux 系統管理中，systemctl 是一個非常有用的命令行工具，它可以幫助管理員更好地了解系統的運行狀態和服務的運行情況。

  以下是一些常用的 `systemctl` 命令：

  `systemctl start service`：啟動一個服務
  `systemctl stop service`：停止一個服務
  `systemctl restart service`：重啟一個服務
  `systemctl status service`：查詢一個服務的狀態
  `systemctl enable service`：將一個服務設置為開機啟動
  `systemctl disable service`：將一個服務設置為不開機啟動
  需要注意的是，systemctl 命令需要以超級用戶權限運行，可以使用 sudo 命令來運行。

- `--firmware-setup`：這個選項指示系統在重新啟動時進入固件設置模式。當系統進入固件設置模式時，您可以更改許多與硬件設置有關的選項，例如啟動順序、CPU 頻率、記憶體時序等等。在固件設置模式下，您可以使用鍵盤和滑鼠進行選擇和更改。

## Windows 11

```cmd
shutdown /r /fw /t 0
```

這是一個使用 `shutdown.exe` 的命令，它告訴 Windows 在關閉電腦之前等待 0 秒（立即關閉），
然後重新啟動並進入 UEFI 固件設置。

這個命令中的參數含義如下：

- `/r`：這個選項表示 Windows 將重啟電腦，而不是直接關閉電腦。
- `/fw`：這個選項表示 Windows 將在重啟後進入 UEFI 固件設置。進入 UEFI 固件設置後，您可以更改許多 BIOS/UEFI 相關的設置。
- `/t 0`：這個選項表示 Windows 不需要等待即可關閉電腦。如果您希望 Windows 等待一段時間後關閉電腦，可以將 /t 參數後面的數字更改為所需的等待時間（以秒為單位）。

總之，`shutdown /r /fw /t 0` 命令會將 Windows 關閉，立即重新啟動，並進入 UEFI 固件設置。如果您希望在進入 UEFI 固件設置之前有一些時間來保存任何未保存的工作，可以將 `/t` 參數後面的數字更改為所需的等待時間。
