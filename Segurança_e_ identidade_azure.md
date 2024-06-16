Segurança e identidade multinuvem com o Azure e o AWS (Amazon Web Services)
Artigo
19/03/2024
10 colaboradores
Neste artigo
Integração de identidade multinuvem
Autenticação forte e validação de confiança explícita
Cloud Platform Security (multinuvem)
Microsoft Defender para Nuvem
Mostrar mais 3
Muitas organizações estão se dando conta de que têm, de fato, uma estratégia de multinuvem, mesmo que essa não tenha sido sua intenção estratégica proposital. Em um ambiente multinuvem, é essencial garantir experiências consistentes de segurança e identidade para evitar mais atritos para desenvolvedores e iniciativas de negócios, além do aumento do risco organizacional proveniente de ataques cibernéticos que aproveitam lacunas de segurança.

O processo de aumentar a consistência da identidade e a segurança entre nuvens deve incluir:

Integração de identidade multinuvem
Autenticação forte e validação de confiança explícita
Cloud Platform Security (multinuvem)
Microsoft Defender para Nuvem
Privileged Identity Management (Azure)
Gerenciamento consistente de identidades de ponta a ponta
Integração de identidade multinuvem
Os clientes que usam as plataformas de nuvem do Azure e do AWS se beneficiam da consolidação dos serviços de identidade entre as duas nuvens usando os serviços do Microsoft Entra ID e de SSO (logon único). Esse modelo permite ter um plano de identidade consolidado por meio do qual o acesso a serviços nas duas nuvens pode ser acessado e administrado de modo consistente.

Essa abordagem permite que os ricos controles de acesso baseados em função no Microsoft Entra ID sejam habilitados nos serviços de IAM (gerenciamento de identidade e acesso) na AWS usando regras para associar os atributos user.userprincipalname e user.assignrole do Microsoft Entra ID a permissões de IAM. Essa abordagem reduz o número de identidades exclusivas que usuários e administradores precisam manter em ambas as nuvens, incluindo uma consolidação da identidade por design de conta que o AWS emprega. A solução de IAM do AWS permite, e identifica especificamente, o Microsoft Entra ID como uma fonte de federação e autenticação para seus clientes.

Um passo a passo completo dessa integração pode ser encontrado no Tutorial: Integração do SSO (logon único) do Microsoft Entra com o AWS (Amazon Web Services).

Autenticação forte e validação de confiança explícita
Como muitos clientes continuam dando suporte a um modelo de identidade híbrida para os serviços do Active Directory, é cada vez mais importante que as equipes de engenharia de segurança implementem soluções de autenticação fortes e bloqueiem métodos de autenticação herdados associados principalmente a tecnologias locais e herdadas da Microsoft.

Uma combinação de políticas de acesso condicional e autenticação multifator permite maior segurança para cenários de autenticação comuns para usuários finais na sua organização. Embora a autenticação multifator forneça um nível maior de segurança para confirmar autenticações, controles adicionais podem ser aplicados usando controles de acesso condicional para bloquear a autenticação herdada para ambientes de nuvem do Azure e do AWS. A autenticação forte usando apenas clientes de autenticação moderna é possível somente com a combinação de políticas de acesso condicional e autenticação multifator.

Cloud Platform Security (multinuvem)
Após uma identidade comum ser estabelecida em seu ambiente multinuvem, o serviço Cloud Platform Security (CPS) do Microsoft Defender para Aplicativos de Nuvem poderá ser usado para descobrir, monitorar, avaliar e proteger esses serviços. Usando o painel de Cloud Discovery, a equipe de operações de segurança pode revisar os aplicativos e recursos que estão sendo usados nas plataformas de nuvem do AWS e do Azure. Após os serviços serem revisados e sancionados para uso, eles poderão ser gerenciados como aplicativos empresariais no Microsoft Entra ID para habilitar o modo de SAML (Security Assertion Markup Language), baseado em senha e de logon único vinculado para conveniência dos usuários.

O CPS também permite avaliar as plataformas de nuvem conectadas quanto a configurações incorretas e à conformidade usando controles de configuração e segurança recomendados específicos do fornecedor. Esse design permite que as organizações mantenham uma exibição consolidada de todos os serviços de plataforma de nuvem e seus status de conformidade.

O CPS também fornece políticas de controle de sessão e acesso para impedir e proteger seu ambiente contra pontos de extremidade ou usuários arriscados quando arquivos mal-intencionados ou exfiltração dos dados são introduzidos nessas plataformas.

Microsoft Defender para Nuvem
O Microsoft Defender para Nuvem fornece gerenciamento de segurança unificado e proteção contra ameaças em suas cargas de trabalho híbridas e de multinuvem, incluindo cargas de trabalho no Azure, no AWS (Amazon Web Services) e na GCP (Google Cloud Platform). O Defender para Nuvem ajuda a localizar e corrigir vulnerabilidades de segurança, aplicar controles de acesso e de aplicativo para bloquear atividades mal-intencionadas, detectar ameaças usando a análise e a inteligência e responder rapidamente a eventuais ataques.

Para proteger seus recursos baseados em AWS no Microsoft Defender para Nuvem, você pode conectar uma conta com a experiência de conectores de nuvem clássicos ou com a página Configurações de ambiente (em versão prévia), o que é recomendado.

Privileged Identity Management (Azure)
Para limitar e controlar o acesso às suas contas com privilégios mais elevados no Microsoft Entra ID, o Privileged Identity Management (PIM) pode ser habilitado para fornecer acesso oportuno aos serviços do Azure. Após implantado, o PIM pode ser usado para controlar e limitar o acesso usando o modelo de atribuição para funções, eliminar o acesso persistente para essas contas privilegiadas e fornecer descoberta e monitoramento adicionais de usuários com esses tipos de conta.

Quando combinados com o Microsoft Sentinel, pastas de trabalho e guias estratégicos podem ser estabelecidos para monitorar e gerar alertas para a equipe do centro de operações de segurança quando houver movimentação lateral de contas que foram comprometidas.

Gerenciamento consistente de identidades de ponta a ponta
Certifique-se de que todos os processos incluam uma exibição de ponta a ponta de todas as nuvens, bem como sistemas locais, e que a equipe de segurança e identidade seja treinada nesses processos.

O uso de uma só identidade no Microsoft Entra ID, em contas do AWS e em serviços locais habilita essa estratégia de ponta a ponta e permite que haja maior segurança e proteção de contas para contas com e sem privilégios. Clientes que buscam reduzir a carga de manutenção de várias identidades em sua estratégia multinuvem adotam o Microsoft Entra ID para fornecer controle consistente e forte, auditoria e detecção de anomalias e abuso de identidades em seus ambientes.

O crescimento contínuo de novos recursos em todo o ecossistema do Microsoft Entra ajuda você a se manter à frente das ameaças ao seu ambiente como resultado do uso de identidades como um plano de controle comum em seus ambientes multinuvem.
