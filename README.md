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
