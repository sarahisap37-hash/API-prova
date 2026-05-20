1. Criar a VPC e Gateway
- Aceda ao console da VPC.

- Clique em Criar VPC e selecione VPC e muito mais.

- Nome: Lab-VPC | Bloco CIDR: 10.0.0.0/16.

- Zonas de Disponibilidade (AZs): Selecione 1.

- Sub-redes Públicas: Selecione 1.

- Sub-redes Privadas: Selecione 0 (Para garantir que sua instância tenha acesso direto à internet).

- Clique em Criar VPC.

 2. Configurar o Firewall (Security Group)
- No menu lateral da VPC, vá em Security Groups > Criar grupo de segurança.

- Nome: SG-API-Livros | VPC: Selecione a Lab-VPC.

- Regras de Entrada (Inbound Rules): Clique em Adicionar regra:
<ol>
  <li>SSH: Porta 22 | Origem: Anywhere-IPv4 (0.0.0.0/0).</li>
  <li>TCP Personalizado: Porta 3000 | Origem: Anywhere-IPv4 (0.0.0.0/0).</li>
</ol>

- Clique em Criar grupo de segurança.

 Lançamento e Configuração da Instância
 Executar a EC2
1. Vá ao console EC2 > Executar instância.
2. AMI: Amazon Linux 2023.
3. Tipo de Instância: t2.micro.

4. Configurações de Rede (Clique em Editar):

- VPC: Lab-VPC.
- Sub-rede: Selecione a sub-rede pública disponível.
- Atribuir IP público automaticamente: Habilitar.
- Grupo de Segurança: Selecionar existente (SG-API-Livros).[
- Clique em Executar instância.

 2. Instalação do Ambiente (Terminal)
Conecte-se à instância via SSH ou EC2 Instance Connect e execute:

```
# Atualizar e instalar Node.js 18
curl -sL https://rpm.nodesource.com/setup_18.x | sudo bash -
sudo yum install -y nodejs

# Criar pasta do projeto
mkdir lab-livros && cd lab-livros
npm init -y
npm install express
```

 Parte 3: Desenvolvimento da Aplicação
1. Criar o Backend
- Digite nano server.js, cole o código abaixo, salve com Ctrl+O, Enter e saia com Ctrl+X.
2. Criar o Frontend

``
 Parte 4: Execução e Teste
1. No terminal, inicie o servidor:
```
node server.js
```
