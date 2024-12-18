import java.util.ArrayList;
import java.util.Date;
import java.util.List;
import java.util.Scanner;
import java.text.ParseException;
import java.text.SimpleDateFormat;

// Classe Veiculo
class Veiculo {
    private String nomeProprietario;
    private String numeroTelefone;
    private int id;
    private String genero;
    private Date dataNascimento;
    private String endereco;
    private String email;
    private Date dataApreensao;
    private String numeroLicenca;
    private String marcaVeiculo;
    private String placaVeiculo;
    private String numeroBI;
    private String infracaoCometida;

    public Veiculo(String nomeProprietario, String numeroTelefone, int id, String genero, Date dataNascimento,
                   String endereco, String email, Date dataApreensao, String numeroLicenca, String marcaVeiculo,
                   String placaVeiculo, String numeroBI, String infracaoCometida) {
        this.nomeProprietario = nomeProprietario;
        this.numeroTelefone = numeroTelefone;
        this.id = id;
        this.genero = genero;
        this.dataNascimento = dataNascimento;
        this.endereco = endereco;
        this.email = email;
        this.dataApreensao = dataApreensao;
        this.numeroLicenca = numeroLicenca;
        this.marcaVeiculo = marcaVeiculo;
        this.placaVeiculo = placaVeiculo;
        this.numeroBI = numeroBI;
        this.infracaoCometida = infracaoCometida;
    }

    // Getters e Setters
    public String getNomeProprietario() { return nomeProprietario; }
    public void setNomeProprietario(String nomeProprietario) { this.nomeProprietario = nomeProprietario; }

    public String getNumeroTelefone() { return numeroTelefone; }
    public void setNumeroTelefone(String numeroTelefone) { this.numeroTelefone = numeroTelefone; }

    public int getId() { return id; }
    public void setId(int id) { this.id = id; }

    public String getGenero() { return genero; }
    public void setGenero(String genero) { this.genero = genero; }

    public Date getDataNascimento() { return dataNascimento; }
    public void setDataNascimento(Date dataNascimento) { this.dataNascimento = dataNascimento; }

    public String getEndereco() { return endereco; }
    public void setEndereco(String endereco) { this.endereco = endereco; }

    public String getEmail() { return email; }
    public void setEmail(String email) { this.email = email; }

    public Date getDataApreensao() { return dataApreensao; }
    public void setDataApreensao(Date dataApreensao) { this.dataApreensao = dataApreensao; }

    public String getNumeroLicenca() { return numeroLicenca; }
    public void setNumeroLicenca(String numeroLicenca) { this.numeroLicenca = numeroLicenca; }

    public String getMarcaVeiculo() { return marcaVeiculo; }
    public void setMarcaVeiculo(String marcaVeiculo) { this.marcaVeiculo = marcaVeiculo; }

    public String getPlacaVeiculo() { return placaVeiculo; }
    public void setPlacaVeiculo(String placaVeiculo) { this.placaVeiculo = placaVeiculo; }

    public String getNumeroBI() { return numeroBI; }
    public void setNumeroBI(String numeroBI) { this.numeroBI = numeroBI; }

    public String getInfracaoCometida() { return infracaoCometida; }
    public void setInfracaoCometida(String infracaoCometida) { this.infracaoCometida = infracaoCometida; }

    @Override
    public String toString() {
        return "Veiculo{" +
                "nomeProprietario='" + nomeProprietario + '\'' +
                ", numeroTelefone='" + numeroTelefone + '\'' +
                ", id=" + id +
                ", genero='" + genero + '\'' +
                ", dataNascimento=" + dataNascimento +
                ", endereco='" + endereco + '\'' +
                ", email='" + email + '\'' +
                ", dataApreensao=" + dataApreensao +
                ", numeroLicenca='" + numeroLicenca + '\'' +
                ", marcaVeiculo='" + marcaVeiculo + '\'' +
                ", placaVeiculo='" + placaVeiculo + '\'' +
                ", numeroBI='" + numeroBI + '\'' +
                ", infracaoCometida='" + infracaoCometida + '\'' +
                '}';
    }
}

// Classe VeiculoDAO
class VeiculoDAO {
    private List<Veiculo> veiculos = new ArrayList<>();

    // Cadastrar Veículo
    public void cadastrarVeiculo(Veiculo veiculo) {
        veiculos.add(veiculo);
    }

    // Listar Veículos
    public List<Veiculo> listarVeiculos() {
        return veiculos;
    }

    // Atualizar Veículo
    public void atualizarVeiculo(int id, Veiculo veiculoAtualizado) {
        for (int i = 0; i < veiculos.size(); i++) {
            if (veiculos.get(i).getId() == id) {
                veiculos.set(i, veiculoAtualizado);
                return;
            }
        }
    }

    // Eliminar Veículo
    public void eliminarVeiculo(int id) {
        veiculos.removeIf(veiculo -> veiculo.getId() == id);
    }
}

// Classe Main
public class Main {
    private static VeiculoDAO veiculoDAO = new VeiculoDAO();
    private static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) throws ParseException {
        boolean exit = false;

        while (!exit) {
            System.out.println("\nDTSER - Sistema de Cadastro de Veículos Apreendidos");
            System.out.println("1. Cadastrar Veículo");
            System.out.println("2. Listar Veículos");
            System.out.println("3. Atualizar Veículo");
            System.out.println("4. Eliminar Veículo");
            System.out.println("5. Sair");
            System.out.print("Escolha uma opção: ");
            int opcao = scanner.nextInt();

            switch (opcao) {
                case 1 -> cadastrarVeiculo();
                case 2 -> listarVeiculos();
                case 3 -> atualizarVeiculo();
                case 4 -> eliminarVeiculo();
                case 5 -> exit = true;
                default -> System.out.println("Opção inválida. Tente novamente.");
            }
        }
    }

    private static void cadastrarVeiculo() throws ParseException {
        System.out.print("Nome do Proprietário: ");
        scanner.nextLine(); // Consome o caractere de nova linha
        String nomeProprietario = scanner.nextLine();
        System.out.print("Número de Telefone: ");
        String numeroTelefone = scanner.nextLine();
        System.out.print("ID: ");
        int id = scanner.nextInt();
        scanner.nextLine(); // Consome o caractere de nova linha
        System.out.print("Gênero: ");
        String genero = scanner.nextLine();
        System.out.print("Data de Nascimento (dd/MM/yyyy): ");
        Date dataNascimento = new SimpleDateFormat("dd/MM/yyyy").parse(scanner.nextLine());
        System.out.print("Endereço: ");
        String endereco = scanner.nextLine();
        System.out.print("Email: ");
        String email = scanner.nextLine();
        System.out.print("Data da Apreensão (dd/MM/yyyy): ");
        Date dataApreensao = new SimpleDateFormat("dd/MM/yyyy").parse(scanner.nextLine());
        System.out.print("Número da Licença ou Carta de Condução: ");
        String numeroLicenca = scanner.nextLine();
        System.out.print("Marca do Veículo: ");
        String marcaVeiculo = scanner.nextLine();
        System.out.print("Placa do Veículo: ");
        String placaVeiculo = scanner.nextLine();
        System.out.print("Número do BI: ");
        String numeroBI = scanner.nextLine();
        System.out.print("Infração Cometida: ");
        String infracaoCometida = scanner.nextLine();

        Veiculo veiculo = new Veiculo(nomeProprietario, numeroTelefone, id, genero, dataNascimento, endereco, email, dataApreensao, numeroLicenca, marcaVeiculo, placaVeiculo, numeroBI, infracaoCometida);
        veiculoDAO.cadastrarVeiculo(veiculo);
        System.out.println("Veículo cadastrado com sucesso!");
    }

    private static void listarVeiculos() {
        System.out.println("\nLista de Veículos Apreendidos:");
        for (Veiculo veiculo : veiculoDAO.listarVeiculos()) {
            System.out.println(veiculo);
        }
    }

    private static void atualizarVeiculo() throws ParseException {
        System.out.print("ID do Veículo a ser atualizado: ");
        int id = scanner.nextInt();
        scanner.nextLine(); // Consome o caractere de nova linha

        System.out.print("Novo Nome do Proprietário: ");
        String nomeProprietario = scanner.nextLine();
        System.out.print("Novo Número de Telefone: ");
        String numeroTelefone = scanner.nextLine();
        System.out.print("Novo Gênero: ");
        String genero = scanner.nextLine();
        System.out.print("Nova Data de Nascimento (dd/MM/yyyy): ");
        Date dataNascimento = new SimpleDateFormat("dd/MM/yyyy").parse(scanner.nextLine());
        System.out[_{{{CITATION{{{_1{](https://github.com/limasuu/inscricao/tree/a153ec4d570036cabc399f635fd9f6c099457cb3/src%2Finscricao%2Fdominio%2FPessoa.java)[_{{{CITATION{{{_2{](https://github.com/pinheirovictor/Trabalho-Web-2019.1/tree/6ded355ae834ffc8878381fd5e0ace5f071d5b4f/Trabalho-final-spring%2Fsrc%2Fmain%2Fjava%2Fbr%2Fcom%2Fufc%2Fmodel%2FPessoa.java)
