# meu-repositorio-iac
repositório para teste com AWS CodePipeline

Repositório feito para atividades da disciplina AWS DevOps do curso MBA em Desenvolvimento Full Stack / Unyleya / ITalents.

**Para a Atividade 3 da disciplina**
*Usando diretamente no AWS CloudFormation*

Passo 1:
    1. Tenha sua conta na AWS e acesse com um usuário que possua políticas adequadas a alterações para criação de pilha e recursos AWS.
    2. Acesse o AWS Management Console.
    3. Navegue até CloudFormation na barra de serviços.

Passo 2: Salve o arquivo 'infaestrutura.yaml' deste projeto

Passo 3: Implantar a Pilha CloudFormation
1. Volte para o Console da AWS e selecione 'Create stack/Criar pilha' em CloudFormation.
2. Escolha 'Upload a template file/Fazer upload de um arquivo de modelo' e faça o upload do arquivo 'infraestrutura.yaml'.
3. Prossiga com as configurações padrão e clique em 'Create stack/Criar pilha'.

Passo 4: Verificar a Criação dos Recursos
Aguarde a criação da pilha e verifique se os recursos foram provisionados corretamente.

**Para a Atividade Final da disciplina**
*Usando AWS CodePipeline*

Passo 1: Clone este repositório no GitHub para um seu.
Passo 2:

 1. Tenha sua conta na AWS.
 2. Acesse o AWS Management Console e navegue até o serviço CodePipeline.
 3. Crie um novo pipeline.
 4. Dê um nome ao pipeline.
 5. Escolha o serviço de versionamento de código GitHub.
 6. Conecte o pipeline ao repositório criado anteriormente.

Passo 3:
 1. Adicione as fases do pipeline:
  - Source: Configurar a origem do código com o repositório.
  - Build: Adicione uma fase de build, conectando ao CodeBuild usando o arquivo 'buildspec.yaml' deste repositório.
  - Deploy: Configure a fase de deploy para aplicar a infraestrutura como código.

  2. Configure a fase de deploy com o 'Provedor de ação' como 'AWS CloudFormatio' e com 'Modo de ação' 'Criar ou atualizar uma pilha'.
  3. Dê um nome à pilha.
  4. Em 'Modelo' o nome do artefato é 'BuildArtifact' e o arquivo deve ser o 'infraestrutura.yaml'
  5. Adicione as capacidades 'CAPABILITY_IAM' e 'CAPABILITY_NAMED_IAM'.
  6. Em 'Nome da função' colocar a 'Role' definida na seção 'IAM' que será a função responsável pelo Deploy, que no caso é a função que irá montar toda a estrutura da CloudFormation.
    O nome da função deve ser um 'ARN' definido na seção 'IAM' do console. Por exemplo: arn:aws:iam::713881787469:role/CodePipeline-CloudFormation-Role
  7. Para terminar a criação do Deploy, apertar o botão 'Concluído'.

     **IMPORTANTE:** na seção 'IAM' a função 'Role' que será responsável pelo Deploy deverá ter permissão a todas as políticas de leitura e escrita de DB RDS, EC2 e LoadBalancer, etc.
    Políticas que foram permitidas ao 'Role': AWSCodePipeline_FullAccess, AWSCodeBuildDeveloperAccess, AWSCloudFormationFullAccess, AmazonVPCFullAccess, AmazonS3FullAccess, AmazonRDSFullAccess e AmazonEC2FullAccess.

Passo 4:
  1. Crie e execute o pipeline:
    Revise as configurações.
    Clique em “Criar pipeline” para concluir a criação.
  2. Teste e Valide o Pipeline
  3. Inicie o pipeline manualmente para verificar se está funcionando conforme o esperado.
  4. Monitore o progresso na interface do CodePipeline.
  5. Verifique a infraestrutura na AWS para confirmar que foi implantada corretamente.

OBS: Você pode gerar alterações no YAML via GitHub que o CodePipeline deve detectar a mudança e iniciar automaticamente o Pipeline e, se tudo der certo, concluir com sucesso um Deploy.
