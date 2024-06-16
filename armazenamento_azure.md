## Armazenamento de dados

Para o Azure Monitor:

- Os dados de métricas são armazenados no banco de dados de métricas do Azure Monitor.
- Os dados de log são armazenados no repositório de logs do Azure Monitor. O Log Analytics é uma ferramenta no portal do Azure que pode consultar esse repositório.
- O log de atividades do Azure é um repositório separado com uma interface própria no portal do Azure.

É possível rotear dados de logs de atividades e de métricas para o repositório de logs do Azure Monitor. Em seguida, é possível usar o Log Analytics para consultar os dados e correlacioná-los com outros dados de log.

Muitos serviços podem usar configurações de diagnóstico para enviar dados de métricas e de logs para outros locais de armazenamento fora do Azure Monitor. Os exemplos incluem o Armazenamento do Azure, os [sistemas de parceiros hospedados](https://learn.microsoft.com/pt-br/azure/partner-solutions/overview) e os [sistemas de parceiros que não são do Azure usando os Hubs de Eventos](https://learn.microsoft.com/pt-br/azure/azure-monitor/essentials/stream-monitoring-data-event-hubs).

Para obter informações detalhadas sobre como o Azure Monitor armazena dados, confira [Plataforma de dados do Azure Monitor](https://learn.microsoft.com/pt-br/azure/azure-monitor/platform/data-platform).





## Métricas de plataforma do Azure Monitor



O Azure Monitor fornece métricas de plataforma para a maioria dos serviços. Essas métricas são:

- Definidas individualmente para cada namespace.

- Armazenadas no banco de dados de métricas da série temporal do Azure Monitor.

- Leves e capazes de dar suporte a alertas quase em tempo real.

- Usadas para acompanhar o desempenho de um recurso ao longo do tempo.

  

**Coleta:** O Azure Monitor coleta as métricas da plataforma automaticamente. Nenhuma configuração é necessária.



**Roteamento:** também é possível rotear as métricas de plataforma para os Logs do Azure Monitor/Log Analytics para consultá-las com outros dados de log. Para obter mais informações, confira a [Configuração de diagnóstico de métricas](https://learn.microsoft.com/pt-br/azure/azure-monitor/essentials/diagnostic-settings#metrics). Para saber como definir as configurações de diagnóstico para um serviço, confira [Criar configurações de diagnóstico no Azure Monitor](https://learn.microsoft.com/pt-br/azure/azure-monitor/essentials/create-diagnostic-settings).



Para obter uma lista de todas as métricas que é possível coletar para todos os recursos no Azure Monitor, confira [Métricas com suporte no Azure Monitor](https://learn.microsoft.com/pt-br/azure/azure-monitor/platform/metrics-supported).



Para obter uma lista das métricas disponíveis para o Armazenamento de Tabelas do Azure, confira [Referência de dados de monitoramento do Armazenamento de Tabelas do Azure](https://learn.microsoft.com/pt-br/azure/storage/tables/monitor-table-storage-reference#metrics).



### Configurações de diagnóstico do Armazenamento de Tabelas do Azure



Ao criar a configuração de diagnóstico, escolha **tabela** como o tipo de armazenamento para o qual deseja habilitar os logs. Em seguida, especifique uma das seguintes categorias de operações para as quais deseja coletar os logs.



Expandir a tabela

| Categoria     | Descrição                     |
| :------------ | :---------------------------- |
| StorageRead   | Ler operações em objetos.     |
| StorageWrite  | Gravar operações em objetos.  |
| StorageDelete | Excluir operações em objetos. |

O grupo de categorias de log de recursos de **auditoria** permite coletar a linha de base dos logs de recursos que a Microsoft considera necessários para a auditoria do recurso. O que é coletado é dinâmico e a Microsoft pode alterá-lo ao longo do tempo à medida que novas categorias de log de recursos se tornam disponíveis. Se você escolher o grupo de categorias de **auditoria**, não poderá especificar nenhuma outra categoria de recurso, pois o sistema decidirá quais logs serão coletados. Para obter mais informações, confira [Configurações de diagnóstico no Azure Monitor: logs de recursos](https://learn.microsoft.com/pt-br/azure/azure-monitor/essentials/diagnostic-settings#resource-logs).



#### Limitações de destino

Para obter limitações gerais de destino, consulte [Limitações de destino](https://learn.microsoft.com/pt-br/azure/azure-monitor/essentials/diagnostic-settings#destination-limitations). As limitações a seguir se aplicam apenas ao monitoramento de contas do Armazenamento do Microsoft Azure.

- Você não pode enviar logs à mesma conta de armazenamento que está monitorando com essa configuração. Essa situação resultaria em logs recursivos nos quais uma entrada de log descreve a gravação de outra entrada de log. Você precisa criar uma conta ou usar outra conta existente para armazenar informações de log.

- Você não pode definir uma política de retenção.

  Se você arquivar logs em uma conta de armazenamento, poderá gerenciar a política de retenção de um contêiner de log definindo uma política de gerenciamento de ciclo de vida. Para saber como, confira [Otimizar custos gerenciando o ciclo de vida de dados automaticamente](https://learn.microsoft.com/pt-br/azure/storage/blobs/lifecycle-management-overview).

  Se você enviar logs para o Log Analytics, poderá gerenciar o período de retenção de dados do Log Analytics no nível do workspace ou até mesmo especificar diferentes configurações de retenção por tipo de dados. Para saber como, consulte [Alterar o período de retenção de dados](https://learn.microsoft.com/pt-br/azure/azure-monitor/logs/data-retention-archive).



## Log de atividades do Azure



O log de atividades contém eventos de nível de assinatura que acompanham as operações de cada recurso do Azure, conforme visto fora desse recurso, por exemplo, criar um recurso ou iniciar uma máquina virtual.

**Coleta:** Os eventos do log de Atividades são gerados e coletados automaticamente em um repositório separado para serem vistos no portal do Azure.

**Roteamento:** você pode enviar dados de log de atividades para os logs do Azure Monitor para analisá-los junto com outros dados de log. Também estão disponíveis outros locais, como o Armazenamento do Microsoft Azure, os Hubs de Eventos do Azure e determinados parceiros de monitoramento da Microsoft. Para obter mais informações sobre como encaminhar o log de atividades, confira [Visão geral do log de atividades do Azure](https://learn.microsoft.com/pt-br/azure/azure-monitor/essentials/activity-log).



## Analisar dados de monitoramento

Existem várias ferramentas para analisar os dados de monitoramento.



### Ferramentas do Azure Monitor

O Azure Monitor dá suporte às seguintes ferramentas básicas:

- [Explorador de Métricas](https://learn.microsoft.com/pt-br/azure/azure-monitor/essentials/metrics-getting-started), uma ferramenta no portal do Azure que permite que você veja e analise as métricas de recursos do Azure. Para obter mais informações sobre essa ferramenta, consulte [Analisar métricas com o explorador de métricas do Azure Monitor](https://learn.microsoft.com/pt-br/azure/azure-monitor/essentials/metrics-getting-started).
- [Log Analytics](https://learn.microsoft.com/pt-br/azure/azure-monitor/learn/quick-create-workspace), uma ferramenta no portal do Azure que permite consultar e analisar dados de log usando o [KQL (Linguagem de Consulta Kusto)](https://learn.microsoft.com/pt-br/azure/data-explorer/kusto/query). Para obter mais informações, consulte [Introdução às consultas de log no Azure Monitor](https://learn.microsoft.com/pt-br/azure/azure-monitor/logs/get-started-queries).
- O [log de atividades](https://learn.microsoft.com/pt-br/azure/azure-monitor/essentials/activity-log), que tem uma interface do usuário no portal do Azure para exibição e pesquisas básicas. Para fazer uma análise mais detalhada, você precisa encaminhar os dados para os logs do Azure Monitor e executar consultas mais complexas no Log Analytics.

As ferramentas que permitem uma visualização mais complexa incluem:

- [Painéis](https://learn.microsoft.com/pt-br/azure/azure-monitor/visualize/tutorial-logs-dashboards), que permitem que você combine diferentes tipos de dados em um único painel no portal do Azure.
- [Pastas de Trabalho](https://learn.microsoft.com/pt-br/azure/azure-monitor/visualize/workbooks-overview), relatórios personalizáveis que você pode criar no portal do Azure. As pastas de trabalho podem incluir texto, métricas e consultas de log.
- [Grafana](https://learn.microsoft.com/pt-br/azure/azure-monitor/visualize/grafana-plugin), uma ferramenta de plataforma aberta que oferece excelência em termos de painéis operacionais. Você pode usar o Grafana para criar painéis que incluem dados de várias fontes além do Azure Monitor.
- [Power BI](https://learn.microsoft.com/pt-br/azure/azure-monitor/logs/log-powerbi), um serviço de análises corporativas que fornece visualizações interativas nas diversas fontes de dados. Você pode configurar o Power BI para importar dados de log automaticamente do Azure Monitor a fim de aproveitar essas visualizações.





### Ferramentas de exportação do Azure Monitor



Você pode obter dados do Azure Monitor em outras ferramentas usando os seguintes métodos:

- **Métricas:** Use a [API REST para métricas](https://learn.microsoft.com/pt-br/rest/api/monitor/operation-groups) para extrair dados de métricas do banco de dados de métricas do Azure Monitor. A API dá suporte a expressões de filtros para refinar os dados recuperados. Para obter mais informações, confira [Referência da API REST do Azure Monitor](https://learn.microsoft.com/pt-br/rest/api/monitor/filter-syntax).
- **Logs:** Use a API REST ou as [bibliotecas de cliente associadas](https://learn.microsoft.com/pt-br/rest/api/loganalytics/query/get?tabs=HTTP).
- Outra opção é a [exportação de dados do workspace](https://learn.microsoft.com/pt-br/azure/azure-monitor/logs/logs-data-export?tabs=portal).

Para começar a usar a API REST para o Azure Monitor, confira [Passo a passo da API REST de monitoramento do Azure](https://learn.microsoft.com/pt-br/azure/azure-monitor/essentials/rest-api-walkthrough?tabs=portal).



### Analisar métricas para o Armazenamento de Tabelas do Azure

As métricas do Armazenamento de Tabelas do Azure estão nestes namespaces:

- Microsoft.Storage/storageAccounts

- Microsoft.Storage/storageAccounts/tableServices

  

Para obter uma lista de todas as métricas com suporte do Azure Monitor, que inclui o Armazenamento de Tabelas do Azure, confira [Métricas compatíveis com o Azure Monitor](https://learn.microsoft.com/pt-br/azure/azure-monitor/essentials/metrics-supported).


