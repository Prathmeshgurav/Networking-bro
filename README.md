while True:
    import socket
    server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    host = socket.gethostname()
    port = 50502
    server.bind((host, port))
    print(f"Binded {host}, {port}")
    server.listen(6)
    # print("Waiting for client...")
    massage, addr = server.accept()
    respond = input("Enter: ")
    ans = massage.send(respond.encode())
    res = massage.recv(1000).decode()
    print(f"Recived from client{addr}: {res}")
    massage.close()
    server.close()
