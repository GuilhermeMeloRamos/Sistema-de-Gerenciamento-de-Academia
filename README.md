# Sistema-de-Gerenciamento-de-Academia
Em função Do Projeto de POO


import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        // ========== 1. Criando Planos ==========
        System.out.println("=== Criando Planos ===");
        Plano mensal = new Plano("Mensal", 120.0, 30);
        Plano trimestral = new Plano("Trimestral", 300.0, 90);
        
        // Testando métodos da classe Plano
        System.out.println(mensal.descricaoPlano());
        System.out.println("Preço mensal: R$" + mensal.getPrecoMensal());
        System.out.println(trimestral.descricaoPlano());
        System.out.println("Preço mensal: R$" + trimestral.getPrecoMensal());
        System.out.println();

        // ========== 2. Criando Instrutores ==========
        System.out.println("=== Criando Instrutores ===");
        Instrutor instrutor1 = new Instrutor("Carlos Silva", "111.222.333-44", "1985-05-15", "123456-G/SP", "Musculação");
        Instrutor instrutor2 = new Instrutor("Ana Paula", "222.333.444-55", "1990-10-20", "654321-G/SP", "Funcional");
        
        // Testando métodos da classe Instrutor
        System.out.println(instrutor1.getNome() + " - " + instrutor1.getTipo());
        System.out.println("Idade: " + instrutor1.getIdade() + " anos");
        System.out.println("CREF: " + instrutor1.getRegistroCREF());
        System.out.println(instrutor2.getNome() + " - " + instrutor2.getTipo());
        System.out.println("Idade: " + instrutor2.getIdade() + " anos");
        System.out.println();

        // ========== 3. Criando Alunos ==========
        System.out.println("=== Criando Alunos ===");
        Aluno aluno1 = new Aluno("João Souza", "333.444.555-66", "1995-02-10", 1001, mensal);
        Aluno aluno2 = new Aluno("Maria Oliveira", "444.555.666-77", "2000-07-25", 1002, trimestral);
        
        // Testando métodos da classe Aluno
        System.out.println(aluno1.getNome() + " - " + aluno1.getTipo());
        System.out.println("Idade: " + aluno1.getIdade() + " anos");
        System.out.println("Matrícula: " + aluno1.getMatricula());
        System.out.println("Plano: " + aluno1.getPlano().getNomePlano());
        System.out.println();

        // ========== 4. Criando Exercícios ==========
        System.out.println("=== Criando Exercícios ===");
        Exercicio supino = new Exercicio("Supino Reto", 4, 12, "Deitado no banco, empurre a barra para cima");
        Exercicio agachamento = new Exercicio("Agachamento Livre", 3, 15, "Desça flexionando os joelhos");
        Exercicio barraFixa = new Exercicio("Barra Fixa", 3, 8, "Puxe o corpo para cima até o queixo passar a barra");
        
        // Testando métodos da classe Exercicio
        System.out.println(supino.detalhesExercicio());
        System.out.println(agachamento.detalhesExercicio());
        System.out.println(barraFixa.detalhesExercicio());
        System.out.println();

        // ========== 5. Criando Treinos ==========
        System.out.println("=== Criando Treinos ===");
        Treino treinoA = new Treino("Treino A - Peito e Tríceps", instrutor1);
        treinoA.adicionarExercicio(supino);
        treinoA.adicionarExercicio(new Exercicio("Crucifixo", 3, 12, "Com halteres, abra os braços"));
        
        Treino treinoB = new Treino("Treino B - Pernas", instrutor2);
        treinoB.adicionarExercicio(agachamento);
        treinoB.adicionarExercicio(new Exercicio("Leg Press", 4, 12, "Empurre a plataforma com as pernas"));
        
        // Testando métodos da classe Treino
        System.out.println(treinoA.resumoTreino());
        System.out.println(treinoB.resumoTreino());
        System.out.println();

        // ========== 6. Gerenciando Academia ==========
        System.out.println("=== Gerenciando Academia ===");
        Academia academia = new Academia();
        
        // Testando métodos da classe Academia
        academia.cadastrarAluno(aluno1);
        academia.cadastrarAluno(aluno2);
        academia.cadastrarInstrutor(instrutor1);
        academia.cadastrarInstrutor(instrutor2);
        academia.adicionarPlano(mensal);
        academia.adicionarPlano(trimestral);
        
        academia.criarTreinoParaAluno(1001, treinoA);
        academia.criarTreinoParaAluno(1002, treinoB);
        
        System.out.println("\n=== Alunos no Plano Mensal ===");
        List<Aluno> alunosMensal = academia.listarAlunosPorPlano("Mensal");
        for (Aluno aluno : alunosMensal) {
            System.out.println(aluno.getNome());
        }
        
        System.out.println("\n=== Todos os Alunos ===");
        for (Aluno aluno : academia.getAlunos()) {
            System.out.println(aluno.getNome() + " - " + aluno.getPlano().getNomePlano());
            System.out.println("Treinos:");
            for (Treino treino : aluno.getTreinos()) {
                System.out.println("- " + treino.getNomeTreino());
            }
        }
    }
}
