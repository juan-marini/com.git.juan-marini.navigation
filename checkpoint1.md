commit 1

eu alterei 3 arquivos porque precisava evoluir a navegação para enviar mais de um dado entre telas. Na MainActivity.kt, importei o NavType e mudei a rota de "perfil/{nome}" para "perfil/{nome}/{idade}" porque agora a tela de Perfil precisava receber tanto o nome quanto a idade do usuário. Defini os tipos explicitamente com navArgument("nome") { type = NavType.StringType } e navArgument("idade") { type = NavType.IntType } dentro de um listOf() para que o Compose Navigation soubesse como interpretar cada argumento corretamente, já que a idade é Int e o nome é String. Recuperei a idade com it.arguments?.getInt("idade", 0). No MenuScreen.kt, alterei a navegação para navController.navigate("perfil/Fulano de Tal/27") porque agora a rota exige os dois valores juntos. Na PerfilScreen.kt, adicionei idade: Int na assinatura e alterei o texto para "PERFIL- $nome tem $idade anos" para que a tela exibisse as duas informações recebidas de forma dinâmica


commit 2

eu alterei apenas o MenuScreen.kt porque o objetivo era testar na prática o parâmetro opcional que eu tinha criado no commit anterior. Mudei o navController.navigate("pedidos") para navController.navigate("pedidos?cliente=Cliente XPTO") para enviar um valor real na navegação. Fiz isso para verificar se a tela de Pedidos conseguia receber e exibir o valor "Cliente XPTO" corretamente, em vez de cair no defaultValue "Cliente Genérico"


commit 3

eu alterei 2 arquivos para implementar um parâmetro opcional na tela de Pedidos. Na MainActivity.kt, importei o navArgument e mudei a rota de "pedidos" para "pedidos?cliente={cliente}" porque eu precisava de um argumento que pudesse ou não ser enviado, sem quebrar a navegação. Usei a sintaxe de query parameter justamente porque é assim que o Compose Navigation diferencia parâmetros opcionais de obrigatórios. Defini um defaultValue = "Cliente Genérico" dentro do navArgument("cliente") para garantir que, caso nenhum valor fosse passado, a tela ainda funcionasse normalmente. Na PedidosScreen.kt, adicionei cliente: String? como nullable na assinatura e alterei o texto para "PEDIDOS - $cliente" para exibir o nome do cliente na tela, seja ele o valor padrão ou um valor enviado pela navegação


commit 4
alterei 3 arquivos para implementar a passagem de parâmetro obrigatório na navegação. Na MainActivity.kt, mudei a rota de "perfil" para "perfil/{nome}" porque eu precisava que a tela de Perfil recebesse um dado dinâmico, e não apenas abrisse estática. Usei it.arguments?.getString("nome", "Usuário Genérico") para recuperar o valor passado na rota e encaminhei para a PerfilScreen. No MenuScreen.kt, alterei o navController.navigate("perfil") para navController.navigate("perfil/Fulano de Tal") porque agora a rota exige que o nome seja enviado junto, caso contrário a navegação falha. Na PerfilScreen.kt, adicionei o parâmetro nome: String na assinatura da composable e alterei o texto para "PERFIL- $nome" para que a tela exibisse dinamicamente o nome recebido em vez de um texto fixo

https://github.com/juan-marini/com.git.juan-marini.navigation