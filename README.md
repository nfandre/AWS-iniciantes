# AWS para iniciantes 2020

### Cloud Computing
Cloud computing é a entrega sob demanda (on demand) de recursos de computação, banco de dados, armazenamento, aplicações ou qualquer outro rercurso de tecnologia que é entregue através de uma plataforma via internet, onde pagamento e preço é baseado em consumo(pay-as-you-go).

   - sob demanda, via plataforma, baseado em consumo

#### Vantagens
 - Mudança na modadalidade de Gastos (Troca de aquisição por serviço - paga o que consome)
 - Economia de escala (Compras em escala enorme)
 - Capacidade
   - Cresce ou diminui a capacidade necessária para atender o negócio
 - Agilidade e velocidade (Recursos estão disponíveis imediatamente)
 - Economia (Sem a necessidade de manter data center)
 - Global em poucos minutos

#### Tipos de Cloud Computing
   - Infraestrutura como serviço - Infrastructure As a Service -IaaS:
     Contratante genrecia os servidores, sejam físicos ou virtuais.
   - Plataforma como Serviço - Plataform As a Service - PaaS: O Contratante é responsável pela aplicação.
   - Software como Serviço - Software As a Service - SaaS: Contratante utiliza produto final.

#### Tipos de instalação
   - Public Cloud - Amazon Web Services, Google Gloud, Microsoft Azure.
   - Hybrid Cloud - Combinação entre Publica e Privada
   - Private Cloud - Normalmente Instalação fisica de um Data Center.


### Principais serviços
- Computação 
- Armazenamento
- Redes e entrega de conteúdo
- Banco de dados

### Infraestrutura da AWS, alcance global
- Regiões (Regions): Localidades físicas onde AWS está disponível
- Zonas de Disponibilidade (Availability Zones - AZ): Quantidade de datacenters que a AWS tem em cada uma das regiões.
- Edge Locations (Pontos de Presença): basicamente uma localidade, em várias partes do mundo, onde é utilizado o serviço de CDN da AWS. CDN - Content Delivery Network, é responsável por acelerar a entrega de conteúdo, principalmente estáticos.

### Modelo de Segurança compartilhado
- AWS é responsável pela segurnça DA Cloud. (Hardware/ AWS Global Infrastructure, Decomissionamento)
- O Cliente é responsável pela segurnça NA Cloud. (Plataformas, applications, identity, acess management)


### Segurança na AWS
- Principais serviços de segurança:

    - AWS IAM - Gestão de Usuários e Acesso
    - AWS Cert Manager - Gestão de Certificados
    - AWS Shield - Proteção contra DDoS
    - AWS WAF - Firewall para Aplicações Web
    - AWS Inspector - Análise de Vulnerabilidades
    - AWS GuardDuty - Monitoração de ameaças baseado em Machine Learning
    - AWS Cognito - Gestão de Acesso para aplicativos móveis integrado com Facebook, Google, AWS, Active Directory, outros.

- Principais serviços de segurança de Rede:
    - Security Groups - Firewall para instâncias EC2 e RDS
    - Network ACL - Controle de Acesso a rede baseado em Regras
    - Rote53 - Proteção a nível de DNS

- CloudTrail - Coleta de Logs de Acesso a Recursos e APIs
- CloudWatch - Monitora e gera alarmes de regras pré-definidas 

AWS Provê conformidade com regras, padrões e leis globais.

#### AWS Identity and Access management (IAM)
- Serviço que controla acesso aos recursos na AWS
- Permite criar e controlar usuários, autenticação ou limitar acesso de usuários a recursos

IAM controla QUEM pode fazer o O QUE na sua conta AWS

- ##### Autenticação (Quem)
    - AWS Management Console 
        - Usuário e Senha
    - AWS CLI ou SDK API
        - Access Key e Secret Key

- ##### Autorização (Permissões)
    - Arquivo JSON
        - Permissões em detalhes
        - Users, Groups e Roles

#### Elementos do IAM:

- #### USERS: Pessoa ou serviço que interage com a AWS:   
        * Nome único
        * Pode ter um conjunto de credenciais
            - Senha da Console da AWS
            - Acces Key (Acesso via SDK ou CLI)
            - MFA - Multi Factor Authentication (Software, Hardware, SMS)
        * Tem que estar associado a apenas uma conta da AWS
        * Permite acesso de forma humana ou programamda (API ou CLI)
  

- #### GROUPS: Grupos de Usuários
        * Agrupa usuários por departamento, função, afinidades, etc
        * Usuários compartilham as mesmas permissões (Policies)
        * Facilitam o gerenciamento de Usuários
- #### POLICIES: Definem QUEM tem acesso AO QUE e O QUE podem fazer (JSON)
        * São descritas no formato JSON
        * Por padrão não dão acesso a nada
        * Podem ser assinaladas para Users, Groups e Roles
        * Definem em detalhes as ações que podem ser executadas
    
    - ##### Tipos de Policies 
        - MANAGED POLICIES 
            - Criadas e Mantidas pela AWS
            - Atualização automática
            - Gerenciamento de Mudança Centralizado
            - Reutilizável
        - INLINE POLICIES
            - Criadas pelos Clientes
            - Permite maior definição e granularidade 
            - Pode ser apagada quando o "principal" for apagado
    

- ##### ROLES: Função/Papel que interage com a AWS
        * Usa as Policies
        * Não possui credencias
        * Chaves de Acesso são criadas dinamicamente
        * Usuários, aplicações e serviços podem assumir IAM Roles

### Serviços de Armazenamento da AWS
Tipos de armazenamentos:
- Objetos:
  As operações devem ser feitas no objeto como um tudo. Ex: delete, upload.
- Em Blocos:
  As operações podem ser feitas em apenas blocos de objeto (partes).
  
Principais Serviços:
- S3 (objetos)
- Glacier (blocos)
- EBS (blocos)
- EFS (Arquivos ou blocos)
- Storage Gateway (Híbrido)
- Snowball (Usado para transferência para AWS - Caixa)
- Snowball Edge (Usado para processamento serviços EC2)
- Snowmobile (Transferência para AWS - Caminhão container)


#### AWS Simple Storage Service S3
Serviço de armazenamento de objetos que permite armazenar e recuperar qualquer quantidade de informações via internet, pagando apenas pelo o que usar.

Informações importantes:

            Provê interface WEB (Console)
            Permite acesso via CLI
            Possui 99.9999999% de Durabilidade
            Possui 99.99% de Disponibilidade
            Permite objetos de até 5TB de tamanho

Conceitos importantes:
- Objetos no S3 são armazenados em Buckets;
- Nomde dos Objetos são chamados de Object Key;
- Versões dos Objetos são chamados de Version ID;
- Endereço dos Objetos são chamados de Link Address.

Definições para objetos e buckets:
- Classe de Armazenamento (storage class)
    - Frequência de acesso
    - Tempo de recuperação
    - Preço
- Política de Acesso (Policy)
- Versionamento
- Criptografia
- Ciclo de Vida (Lifecycle)
    - Permite que ações de gerenciamento de ciclo de vida de objetos possa ser criada à partir de regras


#### AWS Elastic Block Store - EBS
Tipo de armazenamento em blocos, persistente e customizável para instâncias EC2.
- Permite habilitar encriptação(Encryption on Rest)
- Podem ser criadas várias cópias de volume (snapshots)


### Alguns Serviços de Computação na AWS
- EC2
    - Comutador (Máquina virtual)
- ECS
    - Gestão de Containers
- Lambda
    - Serverless
    - FaaS - Function as a Service
    - Cobrado por execução
- Elastic Beanstalk
    - Deploy de aplicações na Web
    - PaaS - Plataformas como Serviço
    - Integração com Git e IDEs

### EC2 - Elastic Compute Cloud
É um serviço que disponibiliza capacidade computacional segura e redimensionável na nuvem.

Modalidades de contratação:
- On Demand
    - Sob Demanda
    - Pay as you Go
- Reservada
    - Reservada por 1 ou 3 anos
    - Descontos
- Spot
    - Leilão
    - define um preço a pagar pela capacidade ociosa da AWS
- Dedicado
    - Servidor Dedicado
    - Preço por hora
