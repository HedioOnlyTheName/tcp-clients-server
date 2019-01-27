# tcp-clients-server
Advanced TCP Client(s) - Server Explanation & Source code of a card game
For powerpoint file (Vietnamese): https://drive.google.com/open?id=1GjOHmTjCbg0WlPwYwnw14MF3GFCxTvM4
About TCP message farming : https://blog.stephencleary.com/2009/04/message-framing.html
Source of a card game: https://drive.google.com/open?id=1O3JYbwUHr3y5PLZm30d5XBkSx0zGHbbc (this is written by me in very different way from Stephen Cleary above which may make you a little more easy to understand).

For examples:
Sender side sends something like this you can split them later on receiver side by '$': Message1$Message2$Message3$
On receiver side, here is how you receive data:

//******************************************************************
byte[] byteReceive = new byte[1024];
                byte[] data_save = new byte[1024]; int index = 0;
                while (s.Connected)
                {
                    int n;
                    if (s.Available > 0)
                    {
                        n = s.Receive(byteReceive);
                    }
                    else { continue; }
                    byte[] tempz = new byte[n];
                    for (int i = 0; i <= tempz.Length - 1; i++)
                    {
                        tempz[i] = byteReceive[i];
                    }
                    Array.Clear(byteReceive, 0, byteReceive.Length);
                    tempz.CopyTo(data_save, index);
                    index += tempz.Length;
                    string test = Encoding.UTF8.GetString(data_save).Replace("\0", "");
                    if (test[test.Length - 1] != '$') { continue; }
                    Array.Clear(data_save, 0, data_save.Length);
                    index = 0;
                    string[] array_save = test.Split('$');
                    new Thread(() =>
                    {
                        foreach (string message in array_save)
                        {
                            if (message.IndexOf("Please connect to Server 1") == 0)
                        }
                    }
           
 //******************************************************************

