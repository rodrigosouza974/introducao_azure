# Criando um Recurso no Azure

Este guia detalha como criar um recurso no Microsoft Azure, desde a configuração inicial até a implantação do recurso desejado. Vamos usar como exemplo a criação de uma máquina virtual (VM), mas as etapas gerais podem ser aplicadas para criar outros tipos de recursos.

## Pré-requisitos

1. **Conta no Azure**: Você precisará de uma conta na plataforma. Se não tiver, pode criar uma [conta gratuita no Azure](https://azure.microsoft.com/free/).
2. **Azure CLI ou Azure Portal**: Para interagir com o Azure, você pode usar a Interface de Linha de Comando (CLI) ou o Portal do Azure.

   - Instale a CLI do Azure seguindo a documentação oficial: [CLI do Azure - Instalação](https://learn.microsoft.com/cli/azure/install-azure-cli)
   - Ou acesse o [Portal do Azure](https://portal.azure.com).

## Passos para Criar um Recurso (Exemplo: Máquina Virtual)

### 1. Logar no Azure

- Via Portal: Acesse o [Portal do Azure](https://portal.azure.com) e faça login com sua conta.

- Via CLI:
    ```bash
    az login
    ```

### 2. Criar um Grupo de Recursos

O grupo de recursos é um container que contém recursos relacionados para um projeto do Azure.

- No Portal: Navegue até "Grupos de Recursos" e clique em "Adicionar".
- Via CLI:
    ```bash
    az group create --name meuGrupoDeRecursos --location eastus
    ```

Para mais informações sobre grupos de recursos: [Documentação Azure Resource Manager](https://learn.microsoft.com/azure/azure-resource-manager/management/overview)

### 3. Criar o Recurso

Vamos criar uma máquina virtual (VM) neste exemplo.

- No Portal: No menu de navegação à esquerda, selecione **Máquinas Virtuais** e depois clique em **Criar**. Preencha os detalhes da máquina virtual, como nome, região e tamanho.

- Via CLI:
    ```bash
    az vm create --resource-group meuGrupoDeRecursos --name MinhaVM --image UbuntuLTS --admin-username azureuser --generate-ssh-keys
    ```

Documentação para criar máquinas virtuais no Azure: [Criando VMs no Azure](https://learn.microsoft.com/azure/virtual-machines/linux/quick-create-cli)

### 4. Configurar Rede e Segurança

Ao criar uma VM, o Azure cria automaticamente recursos de rede, como IP público e grupo de segurança de rede (NSG). Certifique-se de revisar e configurar as regras de entrada e saída para permitir o tráfego necessário.

Para mais detalhes, consulte: [Documentação de Rede do Azure](https://learn.microsoft.com/azure/virtual-network/virtual-networks-overview)

### 5. Acessar a Máquina Virtual

Se estiver usando uma VM Linux, você pode acessar via SSH:

```bash
ssh azureuser@IP_da_VM
```

Para VMs Windows, você pode se conectar usando a Conexão de Área de Trabalho Remota (RDP).

Para mais informações sobre como conectar-se a uma VM no Azure: [Documentação de Conexão a VMs](https://learn.microsoft.com/azure/virtual-machines/linux/ssh-from-windows)

### 6. Monitorar e Gerenciar o Recurso

Use o **Azure Monitor** para acompanhar o desempenho e os logs do seu recurso. Acesse o recurso no Portal do Azure e navegue até a seção **Monitoramento**.

Mais detalhes sobre o Azure Monitor: [Documentação do Azure Monitor](https://learn.microsoft.com/azure/azure-monitor/overview)

### 7. Limpar Recursos

Após concluir seu uso, não se esqueça de excluir os recursos criados para evitar cobranças desnecessárias.

- No Portal: Acesse o grupo de recursos e selecione "Excluir grupo de recursos".
- Via CLI:
    ```bash
    az group delete --name meuGrupoDeRecursos
    ```

## Recursos Complementares

- **Azure Docs**: [Documentação do Azure](https://learn.microsoft.com/azure/)
- **Treinamento Azure**: [Microsoft Learn - Azure](https://learn.microsoft.com/training/paths/azure-fundamentals/)
- **Exemplos de Scripts CLI**: [Exemplos CLI do Azure](https://learn.microsoft.com/cli/azure/azure-cli-samples)

## Conclusão

Este guia oferece uma visão geral de como criar recursos no Azure. Para outros recursos e casos de uso específicos, consulte a documentação oficial e explore as diversas opções que o Azure oferece.
