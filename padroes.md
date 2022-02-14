# Padrões Repositórios e Projeto

- criar pasta local projeto ou workspace
- dentro da pasta criar pasta como nome do projeto. ex. 'projetos/GIM'
- clonar repos do projeto nesta pasta


# Padrões para Desenvolvimento de Dashboards

## Pentaho server

- usar framework 'menMenu' (antigo gamenu)
- criar diretório para cada dashboard do projeto com a seguinte estrutura
  - _style.css_
  - _controller.js_
  - _header.html_
  - _body.html_
- no **Layout Panel** não escrever HTML, CSS e JS em nenhuma hipotse - sempre utilizar os arquivos do framework
- no **Component Panel** 
  - só invocar funcões do _controller.js_
  - nome de componentes usar **camelCase**
- no **Datasource Panel** 
  - nome de query usar **camelCase** com prefixo **q**, ex. 'qVendasDiaria'
- utilizar somente os compnentes genéricos versionados na central de componentes.
  - web-components


# Padrẽos de DW

### Criação de tabelas de dimenssão

- usar em nome de tabelas e campos letras minusculo com palvras separadas por '_' (_underline_)
- usar prefixo **dim_** para tableas de dimenssões
- usar prefixo **fato_** para tabelas fato
- usar prefixo **stage_** para tableas stages

- sequencia dos primeiros campos para tabelas dim_*:

        CREATE TABLE dim_xpto (
              id_xpto BIGSERIAL
            , versao INTEGER
            , data_inicial TIMESTAMP
            , data_final TIMESTAMP
            <outros campos>
        );
        CREATE INDEX idx_dim_xpto_lookup ON dim_xpto(<campos de lookup>);
        CREATE INDEX idx_dim_xpto ON dim_xpto(id_xpto);