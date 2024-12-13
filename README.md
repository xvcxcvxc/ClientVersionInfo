        public static async Task<ClientVersionInfo> Get(Channel channel, string binaryType)
        {
            using (var http = new WebClient())
            {
                string json = await http.DownloadStringTaskAsync($"https://clientsettings.roblox.com/v2/client-version/{binaryType}/channel/{channel}");
                var response = JsonConvert.DeserializeObject<ClientVersionResponse>(json);
                return new ClientVersionInfo(channel, response);
            }
        }
