<!DOCTYPE html>
<html lang="en" class="no-js">

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1.0" />
    <title>CCS + Html5</title>
    <link href='http://fonts.googleapis.com/css?family=Open+Sans:400italic,600italic,700italic,400,600,700' rel='stylesheet' type='text/css'>
    <link href='http://fonts.googleapis.com/css?family=Oswald:400,300' rel='stylesheet' type='text/css'>
    <link rel="stylesheet" href="css/reset.css" />
    <link rel="stylesheet" href="css/style.css" />
    <link rel="stylesheet" href="css/form.css">
</head>

<body>
    <nav class="menu slide-menu-left">
        <ul>
            <li><button class="close-menu">&larr; Voltar</button><br/></li>
            <li><a href="pessoas.php">Contatos</a></li>
            <li><a href="categoria.php">Categorias</a></li>
             <li><a href="produto.php">Produtos</a></li>
        </ul>
    </nav>

    <nav class="menu slide-menu-top">
        <ul>
            <li><button class="close-menu">&uarr; Voltar</button></li>
            <li><a href="Listapessoas.php">Listagem Contatos</a></li>
            <li><a href="pedidos.php">Realizar Pedidos</a></li>
            <li><a href="Listapedidos.php">Listar Pedidos</a></li>
            
        </ul>
    </nav>

    <div id="wrapper">
        <header>
            <div id="title" class="container">
                <h1>Pedidos CSS3</h1>
            </div>
        </header>

        <div id="main">
            <div class="container">                
                <div class="buttons">
                    <button class="nav-toggler toggle-slide-left">Cadastros</button>
                    <button class="nav-toggler toggle-slide-top">Manutenção</button>
                </div><!-- /buttons -->
                <section class="content">
                 <?php
       
                    if ($_POST){
                      $cn =  mysql_connect("localhost", "root", "") or die(mysql_error());
                      mysql_select_db("pedidocompra",$cn) or die(mysql_error()); 

                      $email = $_POST['email'];
                      $nome  = $_POST['nome'];
                      $telefone = $_POST['tel'];     

                      $query = "INSERT INTO `contatos`(`email`, `nome`, `telefone`) VALUES ('".$email."','".$nome."','".$telefone."')";
                      $ok = mysql_query($query);
                      if ($ok){
                        echo '<div class="alert-box success"><span>success: </span>Os dados foram inseridos com sucesso!.</div>';        
                      }
                    }
                    ?>
                    <form class="contact_form" action="pessoas.php" method="post" name="contact_form">

                                <ul>
                                    <li>
                                        <h2>Cadastro de Contatos</h2>
                                     </li>

                                        <li>
                                                <label for="name">Descrição:</label>
                                                <input type="text" name="nome" placeholder="xxxxxxx" required/>
                                        </li>
                                        <li>
                                                <label for="email">Telefone:</label>
                                                <input type="tel" name="tel" placeholder="5555-5555" required pattern="^\(?([0-9]{4})\)?[-. ]?([0-9]{4})$"/>
                                                <span class="form_hint">Requer "5555-5555"</span>
                                        </li>
                                        <li>
                                                <label for="email">Email:</label>
                                                <input type="email" name="email" placeholder="xxxxxx@example.com" required/>
                                                <span class="form_hint">Proper format "name@something.com"</span>
                                        </li>        
                                        <li>
                                            <button class="submit" type="submit" value="enviar">Confirmar</button>

                                        </li>
                                </ul>
                        </form>
                    <div style="display:none;">
                        <a href="https://www.facebook.com/diogo.odelli">Diogo Odelli</a></div>
                    </div>
                </section>
            </div>
        </div>
    </div>
    <script src="js/classie.js"></script>
    <script src="js/js.js"></script>
</body>
</html>
