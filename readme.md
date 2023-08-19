# Descrição
Este projeto é para fazer a configuração pós instalação de uma estação de trabalho XUbuntu. 

Foi baseada na configuração e ferramentas (aplicações) que eu (José Fernandes) uso no meu notebook e na minha estação de trabalho (desktop).

Desta forma, temos 2 versões de configuração: para desktop e para notebook. Em ambas as situações vamos usar 2 playbooks, uma para atualizar e criar o novo usuário e outra para configurar o home do usuário.

Para configurar um host:
- <b>playbook-root.yaml</b>: para atualizar e configurar o S.O., bem como criar o usuário da estação, executa as roles: linux-atualizar, linux-tunning, linux-instalacar_pacotes_padroes e linux-cria_usuario;
- <b>playbook-instalar.yaml</b>: executa as roles para configurar o home do usuário e instlar as aplicações.
- <b>playbook-restaurar.yaml</b>: executa as roles para restaurar o home do usuário e as aplicações.

<br>
<br>

# Instalação e configuração do Ansible

## Instalação

É necessário instalar o Ansible na estação, pois, usamos conecção local, para executar as playbooks.

```bash
sudo apt-add-repository -y ppa:ansible/ansible
sudo apt update
sudo apt -y install ansible
```

As coleções irão ser instaladas de acordo com a necessidade das funções (roles) executadas, contanto que seja discriminada as dependências de cada função no arquivo *meta/main.yaml*. Como no exemplo da função linux-configurar_home:

```yaml
collections:
  - community.general
```

> Atenção para as dependências de pacotes das coleções, pois, estes precisam ser instalados manualmente.

## Configuração 
  
A configuração do ansible está no arquivo ansible.cfg no diretório raiz do projeto, e basicamente diz que todos os arquivos, de configuração ou não, devem estar no diretório do projeto.

Como esse projeto foi pensado para ser executado localmente o inventário tem apenas um host (localhost), e também, os parâmetros para a configuração do host e das aplicações.

# Configuração e execução da playbook

Antes de executar qualquer playbook devemos configurar as credenciais das contas usadas no arquivo vault. Basta seguir o modelo vault-modelo.yaml. Exemplo:

```yaml
# Ansible
ansible_become_pass: 

# Credenciais do novo usuário
vault_user_login: 
vault_user_password: 
vault_user_comment: 
vault_user_uid: 
vault_user_group: 
vault_user_guid: 
vault_user_groups: 
vault_user_key_password: 

# linux-configura_painel
vault_tipo_estacao: 'desktop'

# linux-restaura_backup
vault_path_to_backup: 

# app-apacheds-instalar app-aqua_data_studio-instalar app-dbwrench-instalar app-jmeter-instalar
vault_path_to_downloads: 

# linux-network-configurar_vpn
vpn_domain: 
vpn_user_login: 
# vpn_user_password: 
vpn_group: 
vpn_group_password: 

```

>Onde:<br>
&mdash; <b>vault_user_login</b>: login do usuário da estação, deve ser o mesmo da sua conta no LDAP<br>
&mdash; <b>vault_user_password</b>: senha do usuário da estação, deve ser o mesmo da sua conta no LDAP<br>
&mdash; <b>vault_user_comment</b>: Nome do usuário da estação;<br>
&mdash; <b>vault_user_uid</b>: uid do usuário da estação, deve ser o mesmo da sua conda no LDAP;<br>
&mdash; <b>vault_user_group</b>: grupo principal do usuário da estação, deve ser o mesmo da sua conda no LDAP;<br>
&mdash; <b>vault_user_guid</b>: guid do grupo, deve ser o mesmo do grupo no LDAP;<br>
&mdash; <b>vault_user_groups</b>: grupos (na estação) que o usuário deve pertencer;<br>
&mdash; <b>vault_user_key_password</b>: senha para a SSH key;<br>
&mdash; <b>vault_tipo_estacao</b>: Tipo da configuração do painel no XFCE, pode ser: desktop ou notebook;<br>
&mdash; <b>vault_path_to_backup</b>: Caminho até a pasta do backup que deve ser restaurado;<br>
&mdash; <b>vault_path_to_downloads</b>: Caminho até a pasta de downloads.<br>

>Obs: Estamos usando as credenciais da conta do usuário no LDAP para facilitar futura configuração da autenticação no LDAP.

Executar a playbook como <b>ansible</b>:

```bash
  ansible-playbook -e@tmp/SEU_VAULT.yaml playbook-root.yaml --syntax-check
```

Executar a playbook como o novo usuário:
```bash
  ansible-playbook -e@tmp/SEU_VAULT.yaml playbook-instalar.yaml --syntax-check
```

<br>
<br>

# Funções (roles) disponíveis
|Função|Descrição|restaurar_backup|
| --- | --- | --- |
|app-apache_directory_studio-instalar|Instala o Apache Directory Studio|Sim|
|app-apache_jmeter-instalar|Instala o Apache JMeter||
|app-aqua_data_studio-instalar|Instala o Aqua Data Studio|Sim|
|app-bb_warsaw-instalar|Instala o warsaw para o Banco do Brasil||
|app-dbeaver-instalar|Instala o DBeaver|Sim|
|app-dbwrench-instalar|Instala o DBwrench||
|app-downloadhelper_coapp-instalar|Instala o DownloadHelper Companion app||
|app-firefox-instalar|Instalar o Firefox|Sim|
|app-google_chrome-instalar| instalar o Google Chrome|Sim|
|app-jbosseap6.4-cli-instalar|Instalar o jboss-cli do EAP 6.4||
|app-jbosseap7.1-cli-instalar|Instalar o jboss-cli do EAP 7.1||
|app-libreoffice-restaurar| Restaurar as configurações do LibreOffice||
|app-nautilus-instalar|Instala e configura o Nautilus e extensões|Sim|
|app-nomachine-instalar|Instalar o Nomachine|Sim|
|app-pgadmin4-instalar|Instalar o PgAdmin4 e o postgresql client|Sim|
|app-spotify-instalar|Instalar o Spotify|Sim|
|app-synergy-instalar|Instalar o Synergy|Sim|
|app-terminator-instalar|Instala e configura o Terminator|Sim|
|app-thunderbird-restaurar|Restaura as configurações do Thunderbird||
|app-vim-instalar|Instala e configura o vim||
|app-virtual_box-instalar|Instala o VirtualBox|Sim|
|app-visual_studio_code-instalar|Instala o Visual Studio Code|Sim|
|app-vlc-instalar|Instala o VLC media player|Sim|
|app-vmware_remote_console-instalar|Instalar o VMware Remote Console||
|common|Esta função disponibiliza recursos utilizados por 2 ou mais funções||
|java-instalar_jdk8|Instala a jdk-8||
|linux-atualizar|Atualiza o sistema operacional||
|linux-cria_usuario|Cria o grupo e a conta do usuário da estação||
|linux-home-configurar|Configura o home do usuário||
|linux-home-configura_painel|Configura o painel do home de acordo com o tipo da estação||
|linux-home-restaurar|Restaura o home do usuário||
|linux-instalacar_pacotes_padroes|Instala os pacotes padrões que normalmente uso||
|linux-tunning|Faz a configuração fina do sistema operacional (tunning)||
|

<br>
<br>

# Observações para o backup

Na versão atual deste projeto, o backup da estação deve ter a seguinte estrutura de diretórios, tendo em consideração que estou usando minha estação como exemplo:
<pre>
backup-X/
├── etc
├── home
├── opt
├── u01
└── u02
</pre>

<br>
<br>

# Testes em uma máquina virtual (VM)

Os testes foram executados em uma vm no Virtual Box, onde foram configurados 2 diretórios compartilhados, a origem do backup (path_to_backup) e o diretório deste projeto, facilitando muito os testes realizados. 

Mapeamentos:

| Name | Path | Acces | Auto Mount |
| --- | --- | --- | --- |
|usbhd|/u01|Full|False|
|ansible_workstation|/home/jose.fernandes/projects/github/ansible_workstation-main|Full|False|
|

Os diretórios compartilhados não foram mapeados no fstab, para não prejudicar a inicialização da VM, caso os diretórios alvos não estivessem montados no host hospedeiro.

Criando os pontos de montagem:
```
mkdir /home/${USER}/ansible_workstation 
sudo mkdir /media/${USER}/usbhd -p
```
Montando os diretórios:
```
sudo mount -t vboxsf -o uid=$USER,gid=${USER} usbhd /media/${USER}/usbhd
sudo mount -t vboxsf -o uid=$USER,gid=${USER} ansible_workstation ~/ansible_workstation
```

Obs: a utilização do ${USER} nos comandos shell e do lookup('ansible.builtin.env', 'USER') no playbook, facilitam a execução com os usuários ansible (usuário da instalação) e com o jose.fernandes (usuário novo).

Foi criado um snapshot ao final da instalação do Xubuntu (S.O. instalado), ao final da configuração dos diretórios compartilhados (diretoreios_compartilhados) e ao final da instalação do ansible (ansible_instalado).

As funções (roles) foram inicialmente testadas uma de cada vez, sendo criado um snapshot após a conclusão da execução de cada uma delas.

No fim dos testes das funções, a VM foi restaurada para o snapshot (ansible_instalado) e as playbooks executadas novamente, com todas as funções habilitadas e novamente com um snapshot ao final de cada um.

<br>
<br>

# Referências

https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html

https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_intro.html
https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_blocks.html
https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_loops.html
https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_handlers.html
https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_templating.html
https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_roles.html

https://docs.ansible.com/ansible/latest/collections/ansible/builtin/group_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/user_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/file_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/lineinfile_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/copy_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/enlookup.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/shell_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/template_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_repository_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_key_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/command_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/debug_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/package_facts_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/get_url_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/import_tasks_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/include_tasks_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/get_url_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/stat_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/replace_module.html
https://docs.ansible.com/ansible/latest/collections/ansible/builtin/systemd_service_module.html

https://docs.ansible.com/ansible/latest/collections/community/general/alternatives_module.html
https://docs.ansible.com/ansible/latest/collections/community/general/xfconf_module.html
https://docs.ansible.com/ansible/latest/collections/community/general/snap_module.html

https://docs.ansible.com/ansible/latest/plugins/lookup.html

https://docs.ansible.com/ansible/latest/reference_appendices/playbooks_keywords.html
https://docs.ansible.com/ansible/latest/tips_tricks/ansible_tips_tricks.html

https://techviewleo.com/ansible-check-if-software-package-is-installed/
https://serverfault.com/questions/875247/whats-the-difference-between-include-tasks-and-import-tasks

https://jinja.palletsprojects.com/en/latest/
https://www.edivaldobrito.com.br/java-no-ubuntu-instalar-o-openjdk-8/

https://www.codesandnotes.be/2020/01/13/generate-ssh-keys-using-ansible/