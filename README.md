
class Cliente:
    def __init__(self, nome, empresa, email):
        self.nome = nome
        self.empresa = empresa
        self.email = email

    def __str__(self):
        return f'Cliente: {self.nome} | Empresa: {self.empresa} | Email: {self.email}'


class Funcionario:
    def __init__(self, nome, cargo, email):
        self.nome = nome
        self.cargo = cargo
        self.email = email

    def __str__(self):
        return f'Funcionário: {self.nome} | Cargo: {self.cargo} | Email: {self.email}'

# Define a classe Projeto
class Projeto:
    def __init__(self, nome, cliente, gerente_projeto):
        self.nome = nome
        self.cliente = cliente
        self.gerente_projeto = gerente_projeto
        self.tarefas = []

    def adicionar_tarefa(self, descricao, responsavel):
        tarefa = {"descricao": descricao, "responsavel": responsavel, "status": "não iniciado"}
        self.tarefas.append(tarefa)

    def concluir_tarefa(self, indice_tarefa):
        if 0 <= indice_tarefa < len(self.tarefas):
            self.tarefas[indice_tarefa]['status'] = 'concluído'
        else:
            print("Índice de tarefa inválido.")

    def __str__(self):
        return f'Projeto: {self.nome} | Cliente: {self.cliente.nome} | Gerente: {self.gerente_projeto.nome}'


def main():
    # Criar clientes
    cliente1 = Cliente("Alice Silva", "Tech Innovators", "alice@techinnovators.com")
    cliente2 = Cliente("Bob Souza", "Web Solutions", "bob@websolutions.com")

    # Criar funcionários
    funcionario1 = Funcionario("Carlos Pereira", "Gerente de Projetos", "carlos@empresa.com")
    funcionario2 = Funcionario("Daniela Lima", "Desenvolvedora", "daniela@empresa.com")

    # Criar projetos
    projeto1 = Projeto("Desenvolvimento de Site", cliente1, funcionario1)
    projeto2 = Projeto("App Mobile", cliente2, funcionario1)

    # Adicionar tarefas aos projetos
    projeto1.adicionar_tarefa("Criação do layout", funcionario2)
    projeto1.adicionar_tarefa("Implementação do backend", funcionario2)

    projeto2.adicionar_tarefa("Design do aplicativo", funcionario2)
    projeto2.adicionar_tarefa("Desenvolvimento do frontend", funcionario2)

    # Concluir uma tarefa
    projeto1.concluir_tarefa(0)

    # Exibir informações
    print(cliente1)
    print(funcionario1)
    print(projeto1)
    for tarefa in projeto1.tarefas:
        print(f"Tarefa: {tarefa['descricao']} | Responsável: {tarefa['responsavel'].nome} | Status: {tarefa['status']}")
    
    print("\n" + "="*30 + "\n")

    print(cliente2)
    print(funcionario1)
    print(projeto2)
    for tarefa in projeto2.tarefas:
        print(f"Tarefa: {tarefa['descricao']} | Responsável: {tarefa['responsavel'].nome} | Status: {tarefa['status']}")

if __name__ == "__main__":
    main()
