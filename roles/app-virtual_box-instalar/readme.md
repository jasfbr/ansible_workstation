# Descrição

Instala o VirtualBox

Para restaurar o backup adicionar a opção restaurar_backup no playbook:

Exemplo:
```yaml
  - role: app-virtual_box-instalar
    restaurar_backup: true
```

# Dependências

## Coleções

## Funções

# Variáveis

## Vault

As variáveis que esta função precisa, devem ser colocadas no arquivo vault antes da executção do playbook:

```yaml
user:
  login: 
backup_path:
downloads_path:
```

## Inventário

As variáveis que esta função precisa, devem ser colocadas no inventário antes da executção do playbook:

```yaml
    app:
      virtualbox:
        repository: 'https://download.virtualbox.org/virtualbox/debian {{ansible_distribution_release}} contrib'
        key:
          uri: 'https://www.virtualbox.org/download'
          file: 'oracle_vbox_2016.asc'
```