# Reserva de Salas - Microserviços

Este é um sistema de **reserva de salas** baseado em **microserviços**. O projeto é um **monorepo**, onde cada microserviço possui seu próprio Dockerfile e banco de dados, e todos os serviços são gerenciados por um **docker-compose**.

## Tecnologias Utilizadas
- **Java 17**
- **Spring Boot 3.4.3**
- **PostgreSQL** (um banco para cada serviço)
- **Docker & Docker Compose**
- **Adminer** (para gerenciar os bancos de dados)

## Estrutura do Projeto

```
reserva-salas/
│-- salaservice/       # Microserviço de Sala
|   ├──demo/
│     ├── Dockerfile
│     ├── src/
│-- userservice/       # Microserviço de Usuário
|   ├──demo/
│     ├── Dockerfile
│     ├── src/
│-- reservaservice/    # Microserviço de Reserva
|   ├──demo/
│     ├── Dockerfile
│     ├── src/
│-- docker-compose.yml # Gerencia todos os serviços
│-- README.md          # Documentação do projeto
```

---

## Como Rodar o Projeto 🚀

### 1️⃣ **Gerar os `.jar` de cada microserviço**
Antes de rodar o Docker, compile os microserviços:
```sh
cd .\userservice\demo\ && mvn clean package -DskipTests && cd ..
cd .\salaservice\demo\ && mvn clean package -DskipTests && cd ..
cd .\reservaservice\demo\ && mvn clean package -DskipTests && cd ..
```

### 2️⃣ **Rodar todos os serviços com Docker Compose**
```sh
docker-compose up --build
```
Isso irá subir:
- **3 microserviços** (`userservice`, `salaservice`, `reservaservice`)
- **3 bancos de dados PostgreSQL**
- **Adminer** para gestão do banco

### 3️⃣ **Acessar o Adminer** (Gerenciador de Banco)
- URL: `http://localhost:8080`
- Sistema: **PostgreSQL**
- Servidor: **localhost**
- Usuário: **postgres**
- Senha: **postgres**
- Base de Dados: **userservice**, **salaservice**, **reservaservice**

---

## Testando as APIs no Postman

### **📌 UserService (`8081`)**
#### **Criar um Usuário**
**POST** `http://localhost:8081/users`
```json
{
  "nome": "João Silva",
  "email": "joao@email.com",
  "senha": "123456",
  "telefone": "11987654321",
  "rua": "Rua das Flores",
  "numero": "123",
  "cidade": "São Paulo",
  "cep": "01010-010",
  "cpf": "12345678901",
  "dataNascimento": "1990-05-15",
  "dataCadastro": "2025-03-30"
}
```

#### **Listar Usuários**
**GET** `http://localhost:8081/users`

---

### **📌 SalaService (`8082`)**
#### **Criar uma Sala**
**POST** `http://localhost:8082/salas`
```json
{
  "nome": "Sala de Reunião 1",
  "capacidade": 10
}
```

#### **Listar Salas**
**GET** `http://localhost:8082/salas`

---

### **📌 ReservaService (`8083`)**
#### **Criar uma Reserva**
**POST** `http://localhost:8083/reservas/salvar
```json
{
  "dataHora": "2025-04-01T14:00:00",
  "sala_id": 1,
  "usuario_id": 1
}
```

#### **Listar Reservas**
**GET** `http://localhost:8083/reservas`

---

### **Documentação completa da API no Postman**
A documentação detalhada da API, com exemplos de requisições e respostas, está disponível no Postman.  
Acesse através do link abaixo:

🔗 [Microservices|Reserva de Salas](https://documenter.getpostman.com/view/28679390/2sB2cPkR83)



