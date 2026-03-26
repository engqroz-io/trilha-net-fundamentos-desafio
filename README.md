# DIO - Trilha .NET - Fundamentos
www.dio.me

## Desafio de projeto
Para este desafio, você precisará usar seus conhecimentos adquiridos no módulo de fundamentos, da trilha .NET da DIO.

## Contexto
Você foi contratado para construir um sistema para um estacionamento, que será usado para gerenciar os veículos estacionados e realizar suas operações, como por exemplo adicionar um veículo, remover um veículo (e exibir o valor cobrado durante o período) e listar os veículos.

## Proposta
Você precisará construir uma classe chamada "Estacionamento", conforme o diagrama abaixo:
![Diagrama de classe estacionamento](diagrama_classe_estacionamento.png)

A classe contém três variáveis, sendo:

**precoInicial**: Tipo decimal. É o preço cobrado para deixar seu veículo estacionado.

**precoPorHora**: Tipo decimal. É o preço por hora que o veículo permanecer estacionado.

**veiculos**: É uma lista de string, representando uma coleção de veículos estacionados. Contém apenas a placa do veículo.

A classe contém três métodos, sendo:

**AdicionarVeiculo**: Método responsável por receber uma placa digitada pelo usuário e guardar na variável **veiculos**.

**RemoverVeiculo**: Método responsável por verificar se um determinado veículo está estacionado, e caso positivo, irá pedir a quantidade de horas que ele permaneceu no estacionamento. Após isso, realiza o seguinte cálculo: **precoInicial** * **precoPorHora**, exibindo para o usuário.

**ListarVeiculos**: Lista todos os veículos presentes atualmente no estacionamento. Caso não haja nenhum, exibir a mensagem "Não há veículos estacionados".

Por último, deverá ser feito um menu interativo com as seguintes ações implementadas:
1. Cadastrar veículo
2. Remover veículo
3. Listar veículos
4. Encerrar


## Solução
O código está pela metade, e você deverá dar continuidade obedecendo as regras descritas acima, para que no final, tenhamos um programa funcional. Procure pela palavra comentada "TODO" no código, em seguida, implemente conforme as regras acima.

---

# Configuração de Debug (VSCode)

## 1. Instalação do .NET 6.0

Para debugar a aplicação, é necessário ter o .NET 6.0 SDK instalado em sua máquina.

**Passos de instalação:**
- Acesse o site oficial: https://dotnet.microsoft.com/download/dotnet/6.0
- Faça o download do SDK do .NET 6.0 para seu sistema operacional
- Execute o instalador seguindo as instruções na tela
- Após a instalação, abra um terminal e execute o comando abaixo para verificar a instalação:
  ```
  dotnet --version
  ```
  Você deverá ver a versão do .NET instalada (6.0.x)

## 2. Configuração do arquivo tasks.json

O arquivo `.vscode/tasks.json` define as tarefas de build do projeto.

- Define uma tarefa chamada "build" que executa o comando `dotnet build`
- Compila o projeto especificado em `DesafioFundamentos.csproj`
- Gera caminhos completos para melhorar a legibilidade dos erros de compilação
- É configurada como a tarefa de build padrão do workspace

**Configuração atual:**
```json
{
    "label": "build",
    "command": "dotnet",
    "type": "process",
    "args": [
        "build",
        "${workspaceFolder}/trilha-net-fundamentos-desafio/DesafioFundamentos/DesafioFundamentos.csproj",
        "/property:GenerateFullPaths=true",
        "/consoleloggerparameters:NoSummary"
    ],
    "group": {
        "kind": "build",
        "isDefault": true
    },
    "problemMatcher": "$msCompile"
}
```

## 3. Configuração do arquivo launch.json

O arquivo `.vscode/launch.json` configura o debugador do VS Code para a aplicação.

- **name**: Nome da configuração de debug
- **type**: Define como "coreclr" para aplicações .NET
- **request**: Define como "launch" para iniciar o programa
- **preLaunchTask**: Executa a tarefa de build antes de iniciar o debug (definida no tasks.json)
- **program**: Caminho completo para o arquivo DLL compilado
- **cwd**: Diretório de trabalho da aplicação
- **console**: Define como "integratedTerminal" para usar o terminal integrado do VS Code

**Configuração atual:**
```json
{
    "name": ".NET Core Launch (console)",
    "type": "coreclr",
    "request": "launch",
    "preLaunchTask": "build",
    "program": "${workspaceFolder}/trilha-net-fundamentos-desafio/DesafioFundamentos/bin/Debug/net6.0/DesafioFundamentos.dll",
    "args": [],
    "cwd": "${workspaceFolder}/trilha-net-fundamentos-desafio/DesafioFundamentos",
    "console": "integratedTerminal",
    "stopAtEntry": false
}
```

**Como usar:**
- Abra o arquivo que deseja debugar
- Clique na numeração à esquerda para adicionar breakpoints (pontos de parada)
- Pressione `F5` ou acesse a aba "Run and Debug" para iniciar a sessão de debug
- O programa parará nos breakpoints, permitindo inspecionar variáveis e acompanhar a execução

## 4. Configuração do arquivo launchSettings.json

O arquivo `Properties/launchSettings.json` define as configurações de launch do projeto .NET por padrão e atualmente contém:

- **profiles**: Define os perfis de execução disponíveis
- **DesafioFundamentos**: Nome do perfil de execução
- **commandName**: Define como "Project" para executar como um projeto .NET

**Configuração atual:**
```json
{
    "profiles": {
        "DesafioFundamentos": {
            "commandName": "Project"
        }
    }
}
```

Este arquivo garante que ao executar a aplicação (via `dotnet run` ou através do VS Code), o projeto seja executado corretamente com as configurações padrão do .NET.

