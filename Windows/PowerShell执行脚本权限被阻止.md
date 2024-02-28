问题是：
无法加载文件 `C:\user\<username>\Documents\WindowsPowerShell\profile.ps1`，因为在此系统上禁止运行脚本。有关详细信息，请参阅 https:/go.microsoft.com/fwlink/?LinkID=135170 中的 about_Execution_Policies。

<span class="notation">以下内容来自chatGPT，解决方法被证实有效</span>

你遇到的错误是因为Windows PowerShell的执行策略配置为阻止执行脚本。PowerShell的执行策略是一种安全性配置，用于控制PowerShell脚本的执行。错误消息指出，系统阻止了`C:\user\<username>\Documents\WindowsPowerShell\profile.ps1`文件的执行，这通常是个人的PowerShell配置脚本。

为了解决这个问题，你需要修改PowerShell的执行策略。请按照以下步骤操作：

### 警告

更改执行策略可能会影响Windows的安全性。请确保你了解更改的后果，并且只从可信的来源运行脚本。

### 步骤

1. **以管理员身份打开PowerShell**：
    - 在开始菜单搜索"PowerShell"。
    - 右键点击"Windows PowerShell"，选择"以管理员身份运行"。
2. **查看当前的执行策略**： 执行以下命令以查看当前的执行策略：
```shell
Get-ExecutionPolicy
```
这会显示当前的执行策略。如果是`Restricted`，则表示不允许执行任何脚本。
3. **更改执行策略**： 若要允许脚本执行，你可以将执行策略更改为`RemoteSigned`或`Unrestricted`。`RemoteSigned`是一个相对较安全的选项，它允许运行本地脚本，并且只允许运行经过签名的远程脚本。使用以下命令设置执行策略：
```shell
Set-ExecutionPolicy RemoteSigned
```
系统会提示你确认更改，输入`Y`并回车确认。
4. **验证更改**： 再次运行`Get-ExecutionPolicy`命令以确保执行策略已正确更改。