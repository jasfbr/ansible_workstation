# Descrição

Configura uma conexão de vpn padrão para o linux da prodepa.

Na configuração default, é solicitada a senha do usuário e do grupo.

Para restaurar o backup adicionar a opção restaurar_backup no playbook:

Exemplo:
```yaml
  - role: linux-network-vpn-configurar
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
  group: 
backup_path:
vpn:
  domain: 
  user_login: 
  group: 
```

## Inventário