ALUNO:
class aluno extends pessoa {
    private String matricula;

    protected aluno(String nome, String fone, String cpf, String matricula) {
        super(nome, fone, cpf);
        this.matricula = matricula;
    }

    void saudacao() {
        System.out.println(this.nome + " está aprendendo.");
    }
}

PROFESSOR:
ublic class professor extends aluno {
    private String titulo;

    protected professor(String nome, String fone, String cpf, String matricula,
                        String titulo) {

        super(nome, fone, cpf, matricula);
        this.titulo = titulo;
    }

    void saudacao() {
        System.out.println(nome + " está ensinando.");
    }
}

FUNCIONARIO:
public class Funcionario extends pessoa {
    int cod;
    private String funcao;

    public Funcionario(String nome, String fone, String cpf, int cod, String funcao) {
        super(nome, fone, cpf);
        this.cod = cod;
        this.funcao = funcao;
    }

    void saudacao() {
        System.out.println(nome + " exerce a função de " + funcao);
    }
}

PESSOA:
class pessoa {
    protected String nome;
    protected String fone;
    protected String cpf;

    protected pessoa(String nome, String fone, String cpf) {
        this.nome = nome;
        this.fone = fone;
        this.cpf = cpf;
    }

    void saudacao() {
        System.out.println("Olá, meu nome é " + nome);
    }
}

RESPONSAVEL:
public class Responsavel extends pessoa {
    Aluno[] aluno;

    public Responsavel(String nome, String fone, String cpf, Aluno[] aluno) {
        super(nome, fone, cpf);
        this.aluno = aluno;
    }

    void saudacao() {
        System.out.println(nome + " é responsável por " + aluno.length + " alunos.");
    }
}

MAIN:
import javax.swing.JOptionPane;

public class Main {
    public static void main(String[] args) {

        // Pergunta o tipo de usuário
        String tipo = JOptionPane.showInputDialog(
                null,
                "Escolha o tipo de cadastro:\nAluno, professor, funcionario, responsavel, pessoa",
                "SISTEMA DE CADASTRO",
                JOptionPane.QUESTION_MESSAGE);

        if (tipo == null) return;

        tipo = tipo.toLowerCase();

        // Dados comuns
        String nome = JOptionPane.showInputDialog("Digite o NOME:");
        String fone = JOptionPane.showInputDialog("Digite o FONE:");
        String cpf = JOptionPane.showInputDialog("Digite o CPF:");

        switch (tipo) {

            case "aluno":

                String matAluno = JOptionPane.showInputDialog("Digite a MATRICULA:");

                Aluno a = new Aluno(nome, fone, cpf, matAluno);
                a.saudacao();
                break;

            case "professor":

                String matProf = JOptionPane.showInputDialog("Digite a MATRICULA:");

                String titulo = JOptionPane.showInputDialog("Digite o TITULO:");

                Professor prof = new Professor(nome, fone, cpf, matProf, titulo);

                prof.saudacao();
                break;

            case "funcionario":

                int cod = Integer.parseInt(
                        JOptionPane.showInputDialog("Digite o CODIGO:"));

                String func = JOptionPane.showInputDialog("Digite a FUNÇÃO:");

                Funcionario f = new Funcionario(nome, fone, cpf, cod, func);

                f.saudacao();
                break;

            case "responsavel":

                // Vetor vazio de alunos
                Aluno[] lista = new Aluno[0];

                Responsavel resp = new Responsavel(nome, fone, cpf, lista);

                resp.saudacao();
                break;

            default:

                JOptionPane.showMessageDialog(
                        null,
                        "Tipo inválido.");

                break;
        }
    }
}
