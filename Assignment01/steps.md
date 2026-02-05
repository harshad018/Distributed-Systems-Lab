You accidentally typed **two commands as one line**, so `javac` is treating `AddClient.javarmic` as a class name.

You wrote:

```powershell
javac AddServerIntf.java AddServerImpl.java AddServer.java AddClient.javarmic AddServerImpl
```

You must run them as **two separate commands**:

```powershell
javac AddServerIntf.java AddServerImpl.java AddServer.java AddClient.java
rmic AddServerImpl
```

Step-by-step in `C:\Users\Admin\Downloads\RMIAddExample`:

1. Compile all `.java` files:

   ```powershell
   javac AddServerIntf.java AddServerImpl.java AddServer.java AddClient.java
   ```

2. Generate stub:

   ```powershell
   rmic AddServerImpl
   ```

3. Start registry (new PowerShell window or same, but keep it running):

   ```powershell
   rmiregistry 1099
   ```

4. In another PowerShell window, start server:

   ```powershell
   cd C:\Users\Admin\Downloads\RMIAddExample
   java AddServer
   ```

5. In yet another window, run client:

   ```powershell
   cd C:\Users\Admin\Downloads\RMIAddExample
   java AddClient 6 4
   ```

Run the `javac` and `rmic` exactly as shown (each on its own line) and that annotation-processing error will disappear.