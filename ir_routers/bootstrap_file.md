# Cisco Device Configuration Documentation

## Reset Configuration

### Steps to Reset the Device:

1. **Enter Global Configuration Mode to Set Configuration Register to 0x2102 and Erase the Startup Configuration**
    ```plaintext
    conf t
    config-register 0x2102
    end
    write erase
    ```

2. **Reload the Device:**
    ```plaintext
    reload
    ```

## Basic Configuration

### Steps for Basic Configuration:

1. **Delete Specific Files:**
    ```plaintext
    delete /f before-*
    delete /f /r archive*
    ```

2. **Create Directory for Archive:**
    ```plaintext
    mkdir archive
    ```

3. **Configure Archive Settings:**
    ```plaintext
    conf t
    archive
    path flash:/archive
    maximum 8
    end
    ```

4. **Configure IP Hosts:**
    ```plaintext
    conf t
    ip host fndserver.fndiot.com 10.76.108.147
    ip host tps.fndiot.com 10.76.108.148
    ip host caserver.fndiot.com 10.76.108.152
    ```

5. **Configure Interface `gi0` with IP Address and Bring it Up:**
    ```plaintext
    interface gi0
    ip address 10.76.108.111 255.255.255.0
    no shut
    exit
    ```

6. **Configure PnP Profile for Zero-Touch Deployment:**
    ```plaintext
    pnp profile pnp-zero-touch
    transport http ipv4 10.76.108.148 port 9125
    end
    ```

7. **Save Configuration:**
    ```plaintext
    wr
    ```

8. **Ping the Host to Verify Connectivity:**
    ```plaintext
    ping 10.76.108.147
    ```

