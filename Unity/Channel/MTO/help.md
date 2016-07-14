## MTO 帮助系统说明

### 登录支持接口列表

| 序号 | 方法名 | 方法说明 | 是否支持 | 备注 |
| :--: | -- |:-------: | :-----: | -- |
| 1 | public bool Initialize() | 初始化方法 | √ | - |
|2||public void Send(string content)|发关反馈||

       

        public void Send(string content)
        
        public void GetNewMessageCount(FeedbackCallback callback)
       
        public void OnGetNewMessageCount(string result)
       
        public void SetLanguage(string language)
       

        public void ShowHelpCenter(string channel = "IMSDK")
        
        public void SetChannel(string channel = "IMSDK")
        
        public string GetLanguage()
        public void SetZone(string zone)

        public string GetZone()

        public void SetRoleName(string roleName)

        public string GetRoleName()

        public void SetRoleId(string roleId)

        public string GetRoleId()

        public void SetServerId(string serverId)

        public string GetServerId()

        public void SetServerName(string serverName)

        public string GetServerName()
        public void SetLevel(string level)

        public string GetLevel()

		public void ShowHelpCenter(string extraJson,string channel,HelpCallback callback = null)

		public void ShowFAQ(string extraJson = "",HelpCallback callback = null)

		public void ShowCustomerService(string extraJson = "",HelpCallback callback = null)
        
		private void OnHelpCenter(string result)

       

