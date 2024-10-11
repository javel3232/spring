@Controller
public class OrderController {

    @GetMapping("/orders")
    public String showOrders(Model model) {
        List<Order> orders = Arrays.asList(
            new Order("0504801", 1, "14961", "PA PREVENTA HABITAT 103", "Octubre", "Quality", "Alistado", "ACH", "10/10/2024", "LACAGUTI"),
            new Order("0504802", 5, "7102", "LA PINTADA", "Octubre", "Synergy", "Nivel I", "ACB", "10/10/2024", "LACAGUTI"),
            // Add more orders here...
        );
        
        model.addAttribute("orders", orders);
        return "orders";
    }
}

public class Order {
    private String orden;
    private int documentos;
    private String codigo;
    private String fideicomiso;
    private String mesaCausar;
    private String mesa;
    private String estado;
    private String tipologia;
    private String fechaCumplimiento;
    private String usuario;

    // Constructor, getters, and setters
}


<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org" lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Front Formulario Web - Grupo Bancolombia</title>
    <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
    <style>
        .btn-yellow { background-color: #ffc107; border-color: #ffc107; }
        .btn-yellow:hover { background-color: #e0a800; border-color: #d39e00; }
        .table-header { background-color: #343a40; color: white; }
    </style>
</head>
<body>
    <div class="container-fluid mt-3">
        <div class="row align-items-center mb-3">
            <div class="col-auto">
                <img src="/path-to-your-logo.png" alt="Logo" height="50">
            </div>
            <div class="col">
                <h1 class="mb-0">Front Formulario Web</h1>
            </div>
            <div class="col-auto">
                <img src="/path-to-bancolombia-logo.png" alt="Grupo Bancolombia" height="50">
            </div>
        </div>
        
        <div class="row mb-3">
            <div class="col">
                <button class="btn btn-yellow mr-2">
                    <i class="fas fa-file-export"></i> EXPORTADO A GESTOR
                </button>
                <div class="d-inline-block mr-2">
                    <input type="text" class="form-control" placeholder="Búsqueda orden...">
                </div>
                <button class="btn btn-yellow mr-2">CELULAS DE TRABAJO ▼</button>
                <button class="btn btn-yellow mr-2">TIPOLOGÍA ▼</button>
                <button class="btn btn-yellow mr-2">USUARIO ▼</button>
                <button class="btn btn-dark">ESTADO ▼</button>
            </div>
        </div>
        
        <div class="table-responsive">
            <table class="table table-striped table-bordered">
                <thead class="table-header">
                    <tr>
                        <th>#</th>
                        <th>Orden</th>
                        <th>Documentos</th>
                        <th>Código</th>
                        <th>Fideicomiso</th>
                        <th>Mesa Causar</th>
                        <th>Mesa</th>
                        <th>Estado</th>
                        <th>Tipología</th>
                        <th>Fecha de Cumplimiento</th>
                        <th>Usuario</th>
                    </tr>
                </thead>
                <tbody>
                    <tr th:each="order, iterStat : ${orders}">
                        <td th:text="${iterStat.count}"></td>
                        <td th:text="${order.orden}"></td>
                        <td th:text="${order.documentos}"></td>
                        <td th:text="${order.codigo}"></td>
                        <td th:text="${order.fideicomiso}"></td>
                        <td th:text="${order.mesaCausar}"></td>
                        <td th:text="${order.mesa}"></td>
                        <td th:text="${order.estado}"></td>
                        <td th:text="${order.tipologia}"></td>
                        <td th:text="${order.fechaCumplimiento}"></td>
                        <td th:text="${order.usuario}"></td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>

    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.3/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
    <script src="https://kit.fontawesome.com/your-fontawesome-kit.js"></script>
</body>
</html>
