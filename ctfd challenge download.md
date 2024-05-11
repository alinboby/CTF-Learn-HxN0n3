## ctfdget

### official link
    https://github.com/HanEmile/ctfdget

### steps
    └─$ go build ./...
    go: downloading gopkg.in/h2non/gentleman.v2 v2.0.4
    go: downloading golang.org/x/net v0.0.0-20200625001655-4c5254603344

    └─$ ls
    ctfdget  go.mod  go.sum  LICENSE  main.go  README.md  structs.go

    └─$ ctfdget            
    ctfdget: command not found

    └─$ ./ctfdget             
    Fetching all challenges using the ctf api...
    Request error: Get "https://ctf.example.com/api/v1/challenges": dial tcp: lookup ctf.example.com on 192.168.37.2:53: no such host
    panic: Get "https://ctf.example.com/api/v1/challenges": dial tcp: lookup ctf.example.com on 192.168.37.2:53: no such host

    goroutine 1 [running]:
    main.main()
            /mnt/hgfs/CTF/CTF-events/ctfdget/ctfdget-master/main.go:27 +0x52b

    └─$ ./ctfdget --help
    Usage of ./ctfdget:
      -out string
            The name of the folder to dump the files to (default "challdump")
      -session string
            The session (the value of the cookie named 'session') (default "9e8831af-ce30-48c3-8663-4b27262f43f1.pjKPVCYufDhuA9GPJAlc_xh45M8")
      -url string
            The root URL of the CTFd instance (default "https://ctf.example.com")


### download/fetch all challenges

    └─$ go run ./... -session 3df26dd2-5072-4576-b4a1-2ca77db5fb83.ojMavLcv0t6BUTO0dOtM21O4Q_0 -url https://ctf.ingonyama.com -out ingonyama
    Fetching all challenges using the ctf api...
    Done fetching all challenges
    Downloading the files included in the challenges
    → ingonyama/ZK/It is over 9000!
    → ingonyama/General Cryptography/Safe bn254
    → ingonyama/Fun/Umculo
    → ingonyama/Fun/The Power of iNTEgers 
    → ingonyama/OSINT/Lost Funds
    → ingonyama/ZK/The Day of Sagittarius IV
    → ingonyama/Web/ZokClub
    → ingonyama/ZK/Operation ZK rescue
    → ingonyama/General Cryptography/The Lost Relic
    → ingonyama/ZK/A Tale of Two Keys
    → ingonyama/ZK/Loki's Vault 
    

