while True:
                import socket
                server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
                host = socket.gethostname()
                port = 50501
                server.connect((host, port))
                print(f"connected to {host},{port}")
                rev = server.recv(1000).decode()
                print(f"Recived from server: {rev}")
                massage = input("Enter:")
                ju = server.send(massage.encode())
                server.close()
