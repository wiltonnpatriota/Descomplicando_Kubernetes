Role: windows_patch
===================

Role para buscar e aplicar atualizações do sistema Windows usando o módulo `win_updates` e reiniciar quando necessário.

Uso
----

Inclua a role em um playbook direcionado a hosts Windows. Exemplo:

```yaml
- name: Aplicar patches no Windows
  hosts: windows
  gather_facts: no
  roles:
    - role: windows_patch
      # opcional: sobrescrever defaults aqui
      windows_update_allow_reboot: true
```

Variáveis principais (em `defaults/main.yml`):
- `windows_update_categories`: lista de categorias a instalar (padrão: Critical, Security)
- `windows_update_kb_filter`: string para filtrar KBs específicos (padrão: vazio)
- `windows_update_source`: fonte de atualizações
- `windows_update_allow_reboot`: permitir reinício automático
- `windows_update_reboot_timeout`: timeout do reboot (segundos)

Exemplo de inventory (WinRM):

```
[windows]
winserver ansible_host=10.0.0.10 ansible_user=Administrator ansible_password=Secret ansible_connection=winrm ansible_winrm_transport=ntlm ansible_winrm_server_cert_validation=ignore
```
