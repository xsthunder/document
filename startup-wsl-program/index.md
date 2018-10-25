
see https://stackoverflow.com/questions/48757892/windows-how-to-automatic-satrt-apache2-in-ubuntu-windows
open-startup-directory.cmd
@in win + r enter "shell:common startup"

explorer C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp

see https://github.com/Microsoft/WSL/issues/511#issuecomment-239348586
start-htps.cmd
bash.exe -c 'bash /home/xs/linux-setting/wsl/start-hpts.sh; bash'


start-jupyter-notebook.cmd
bash.exe -c 'bash /home/xs/linux-setting/wsl/start-jupyter-notebook.sh; bash'


