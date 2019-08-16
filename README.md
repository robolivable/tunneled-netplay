### Server steps
Remote forward:

    ssh -R 33420:localhost:33469 <EC2 public ip>

Putty config for remote forward (server host):

    Host Name => <EC2 public ip>
    Port => 22
    SSH > Auth > Private key => <PPK file>
    Tunnels =>
        x Local ports accept connections from other hosts
        x Remote ports do the same
        Forwarded ports:
            R33420 localhost:33469

Emu:

    /server 33469

### Client steps
Local forward:

    ssh -L 33420:localhost:33420 <EC2 public ip>

Putty config for remote forward (client host):

    Host Name => <EC2 public ip>
    Port => 22
    SSH > Auth > Private key => <PPK file>
    Tunnels =>
        x Local ports accept connections from other hosts
        x Remote ports do the same
        Forwarded ports:
            L33420 localhost:33420

Emu:

    /connect 127.0.0.1 33420

### 3rd party server required
Using EC2, you can configure a secure tunnel between two clients. Connecting over putty 
requires a PPK file (which can be generated using a PEM file obtained by AWS for 
connecting to the instance using putty-gen). The EC2 server only needs sshd running to
forward all tunneled packets.

#### Resource links
https://mariopartynetplay.com/n64.htm

https://serverfault.com/questions/387772/ssh-reverse-port-forwarding-with-putty-how-to-specify-bind-address

https://linuxacademy.com/guide/17385-use-putty-to-access-ec2-linux-instances-via-ssh-from-windows/

https://unix.stackexchange.com/questions/115897/whats-ssh-port-forwarding-and-whats-the-difference-between-ssh-local-and-remot
