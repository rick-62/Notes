
## Overview
When using Docker in Windows, WSL is responsible for allocating memory and CPU. By default there is no limit to the amount of memory which can be allocated. Over time memory allocation can creep up until there is barely anything left for the host OS.

## Resolve WSL resource issue
To set the allocation limits to WSL:
1. Navigate to User folder (C:/Users/user-name)
2. Create blank `.wslconfig` file
3. Add the following to the config file:
    ```powershell   
    [wsl2]
    memory=2GB
    processors=2
    ```
4. Open Powershell with admin rights
5. execute command `Restart-Service LxssManager` (restarts WSL)

## Other useful commands
```bash
# shutdown WSL
wsl --shutdown
```


