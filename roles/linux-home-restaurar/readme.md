# Descrição

Configura o painel do XFCE de acordo com os meus padrões.

# Dependências

## Coleções

## Funções

- linux-home-configurar
- linux-home-configurar_painel

# Variáveis

Esta função necessita de variáveis que estão no inventário e no arquivo vault,
elas devem ser informadas antes de executar a função.

As variáveis no inventário são carregadas com o ansible_facts:

```yaml
current_desktop: '{{ansible_env.XDG_CURRENT_DESKTOP | lower}}'
```

## Vault:

```yaml
user:
  login: 
  group: 
backup_path: 
```

## Inventário
