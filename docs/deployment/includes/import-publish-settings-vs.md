
1. 您有 Visual Studio 中開啟 ASP.NET 專案的電腦，以滑鼠右鍵按一下方案總管 中的專案，然後選擇**發佈**。

1. 如果您先前已設定任何發行的設定檔**發佈**窗格隨即出現。 按一下 **建立新的設定檔**。

1. 在 [**挑選發行目標**] 對話方塊中，按一下**匯入設定檔**。

    ![選擇發行](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. 瀏覽至您在上一節中建立的發行設定檔的位置。

1. 在 [**匯入發行設定檔**] 對話方塊中，瀏覽至並選取您在上一節中建立的設定檔，然後按一下**開啟**。

    Visual Studio 隨即開始部署程序和輸出視窗會顯示進度和結果。

    如果您取得的任何部署錯誤，請按一下**設定**編輯設定。 修改設定，然後按一下**驗證**來測試新的設定。 如果找不到主機名稱，請嘗試 IP 位址，而不是中的主機名稱**伺服器**並**目的地 URL**欄位。

    ![在 [發行] 工具中編輯設定](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
