---

# Configurando uma Instância de Banco de Dados no Azure

Este guia orienta sobre como configurar uma instância de banco de dados no Microsoft Azure. Utilizaremos o **Azure SQL Database** como exemplo, mas você pode aplicar um processo similar para outros serviços de banco de dados no Azure, como o **MySQL**, **PostgreSQL** ou **Cosmos DB**.

## Pré-requisitos

1. **Conta no Azure**: Se você ainda não tem uma conta no Azure, pode criar uma gratuitamente aqui: [Conta gratuita do Azure](https://azure.microsoft.com/free/).

2. **Ferramenta de Gerenciamento**:
   - Acesse o [Portal do Azure](https://portal.azure.com).
   - Ou instale a CLI do Azure: [Azure CLI - Instalação](https://learn.microsoft.com/cli/azure/install-azure-cli).

## Passos para Configurar uma Instância de Banco de Dados

### 1. Criar um Grupo de Recursos

Antes de criar a instância do banco de dados, crie um **Grupo de Recursos** para organizar os recursos do Azure.

- No **Portal do Azure**: Vá até **Grupos de Recursos** > **Criar**. Defina o nome do grupo e a região.

- Na **CLI**:
    ```bash
    az group create --name meuGrupoDeRecursos --location eastus
    ```

Saiba mais sobre grupos de recursos: [Documentação de Grupos de Recursos](https://learn.microsoft.com/azure/azure-resource-manager/management/manage-resource-groups-portal)

### 2. Criar a Instância de Banco de Dados SQL (Azure SQL Database)

#### No Portal do Azure:

1. No menu lateral esquerdo, clique em **"Criar um recurso"**.
2. Pesquise por "SQL Database" e clique em **Criar**.
3. Preencha os seguintes campos:
    - **Assinatura**: Selecione sua assinatura do Azure.
    - **Grupo de Recursos**: Selecione o grupo de recursos criado anteriormente.
    - **Nome do Banco de Dados**: Defina o nome para sua instância de banco de dados.
    - **Servidor**: Selecione "Criar Novo" e preencha as informações para o servidor SQL.
    - **Tipo de Preço**: Escolha a camada de desempenho (Basic, Standard ou Premium) de acordo com suas necessidades.

4. Configure a autenticação (usuário e senha) e clique em **Revisar + Criar**.

#### Na CLI:

Você pode criar uma instância SQL com a CLI do Azure usando o comando abaixo:

```bash
az sql server create --name meuServidorSQL --resource-group meuGrupoDeRecursos --location eastus --admin-user admin123 --admin-password MinhaSenhaSegura!
```

Após a criação do servidor, crie um banco de dados:

```bash
az sql db create --resource-group meuGrupoDeRecursos --server meuServidorSQL --name meuBancoDeDados --service-objective S0
```

Documentação sobre a criação de SQL Database: [Documentação do Azure SQL Database](https://learn.microsoft.com/azure/azure-sql/database/)

### 3. Configurar Regras de Firewall

Você precisará permitir que o IP do seu dispositivo (ou faixa de IPs) tenha acesso ao banco de dados, configurando o firewall do servidor SQL.

#### No Portal do Azure:

1. No menu de navegação da instância do servidor SQL, selecione **Configurações de Firewall e Redes Virtuais**.
2. Clique em **Adicionar Regra de Firewall**.
3. Insira o nome da regra e o intervalo de IP permitido (ex.: o IP da sua máquina local).

#### Na CLI:

Você também pode configurar o firewall via CLI:

```bash
az sql server firewall-rule create --resource-group meuGrupoDeRecursos --server meuServidorSQL --name RegraDeAcesso --start-ip-address <seu-IP> --end-ip-address <seu-IP>
```

Para mais informações: [Configurar regras de firewall no Azure SQL](https://learn.microsoft.com/azure/azure-sql/database/firewall-configure)

### 4. Conectar ao Banco de Dados

Agora que o banco de dados está configurado e o firewall está definido, você pode se conectar à instância.

#### Usando o **SQL Server Management Studio (SSMS)**:
1. Abra o SSMS.
2. Clique em **Conectar ao Servidor**.
3. No campo **Servidor**, insira o nome do servidor no formato `<seu-servidor>.database.windows.net`.
4. Insira o nome de usuário e senha configurados anteriormente.

#### Usando **Azure Data Studio**:
1. Abra o Azure Data Studio.
2. Vá até **Conectar** e preencha o campo do servidor com o nome no formato `<seu-servidor>.database.windows.net`.
3. Preencha o nome de usuário e senha.

#### Usando a **CLI do Azure**:
Você pode conectar-se via CLI usando o comando:

```bash
az sql db show-connection-string --server meuServidorSQL --name meuBancoDeDados --client sqlcmd
```

Esse comando gera uma string de conexão que pode ser usada no terminal para se conectar via `sqlcmd`.

### 5. Monitorar e Gerenciar o Banco de Dados

Use o **Azure Monitor** para acompanhar o desempenho, métricas e logs do seu banco de dados:

- No Portal do Azure, vá até seu banco de dados e selecione **Monitoramento** no painel lateral.
- A partir daqui, você pode visualizar o uso de CPU, IO, transações e outros indicadores importantes.

Para mais informações: [Monitorar SQL Database](https://learn.microsoft.com/azure/azure-sql/database/monitor-tune-overview)

### 6. Limpar Recursos

Para evitar cobranças indesejadas, é recomendável excluir recursos que você não está mais utilizando.

- No **Portal do Azure**: Acesse seu grupo de recursos e selecione **Excluir Grupo de Recursos**.
- Na **CLI**:
    ```bash
    az group delete --name meuGrupoDeRecursos
    ```

## Recursos Complementares

- **Documentação do Azure SQL**: [Azure SQL Database](https://learn.microsoft.com/azure/azure-sql/database/)
- **Documentação do Banco de Dados MySQL**: [Azure Database for MySQL](https://learn.microsoft.com/azure/mysql/)
- **Documentação do Banco de Dados PostgreSQL**: [Azure Database for PostgreSQL](https://learn.microsoft.com/azure/postgresql/)
- **Treinamento Azure**: [Microsoft Learn - Banco de Dados no Azure](https://learn.microsoft.com/training/paths/azure-sql-fundamentals/)

---