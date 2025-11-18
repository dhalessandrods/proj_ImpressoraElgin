# 🖨️ Sistema CLI Impressora Elgin i9
**Controlador CLI super amigável para Impressora Térmica Elgin i9 (via DLL)**

Um programa em Java puro que transforma as funções da DLL oficial da Elgin i9 em um menu simples, intuitivo e extremamente fácil de usar.  
Perfeito para quem quer testar todas as funções da impressora (texto, QR Code, código de barras, XML SAT, gaveta, beep etc.) sem precisar escrever uma linha de código toda vez.
****
> “Finalmente consigo fazer a impressora fazer tudo que eu quero só digitando números!”  
> — Você, daqui a 2 minutos

## 🎯 Objetivo do projeto
Criar a forma **mais simples e humana possível** de interagir com todas as funções da impressora térmica Elgin i9 usando a DLL oficial, sem precisar montar strings complicadas ou lembrar parâmetros toda hora.

O foco é ser **rápido de aprender**, mesmo para quem nunca programou na vida. Basta abrir, escolher o número da função e testar na hora.

## 🛠️ Tecnologias utilizadas
- **Java 8+** (100% puro, sem frameworks)
- **JNA** (Java Native Access) – para carregar e usar a DLL da Elgin
- **Documentação Elgin**: Utilizado como auxílio para desenvolver o programa (https://elgindevelopercommunity.github.io/group___m1.html) 

## 📦 Dependências necessárias
- **JNA** → `jna-5.13.0.jar` + `jna-platform-5.13.0.jar` (já incluídos no repositório ou baixe em https://github.com/java-native-access/jna)
- **DLL da Elgin** → `E1_Impressora01.dll` (vem com o driver oficial da i9 – versão testada: 1.0.0.56)

## 🚀 Como executar (passo a passo ridiculamente simples)

1. Baixe ou clone este repositório
2. Abra o IntelliJ (ou Eclipse, NetBeans, VS Code com Java, o que preferir)
3. Importe a pasta do repositório como projeto Java
4. Coloque a DLL `E1_Impressora01.dll` em um local fixo do seu PC
5. Altere a linha do código (linha ~35) para o caminho correto da sua DLL:
   ```java
   Native.load("C:\\Seu\\Caminho\\E1_Impressora01.dll", ImpressoraDLL.class);
   ```
6. Execute a classe `Main.java`
7. Pronto! O menu aparece e você já pode usar tudo!

> Dica de ouro: deixe a DLL dentro da pasta do projeto e use caminho relativo:
> ```java
> Native.load("E1_Impressora01.dll", ImpressoraDLL.class);
> ```

## 📟 Menu principal (o que você vai ver na tela)

```
************************************
*        MENU DA IMPRESSORA        *
************************************
1 - Configurar Conexão
2 - Abrir Conexão
3 - Impressão Texto
4 - Impressão QRCode
5 - Impressão Cod Barras
6 - Impressão XML SAT
7 - Impressão XML Cancelamento SAT
8 - Abrir Gaveta Elgin
9 - Abrir Gaveta (padrão)
10 - Sinal Sonoro (beep)
11 - Obter Versão DLL
0 - Fechar Conexão e Sair
```

Todas as funções já avançam o papel e cortam automaticamente após imprimir.  
Você literalmente só digita o número e o texto quando solicitado. Fim.

## ⚙️ Funcionalidades já implementadas e testadas

| Opção | Função                        | O que acontece                                                                |
|-------|-------------------------------|-------------------------------------------------------------------------------|
| 1     | Configurar Conexão            | Usuário digita os parâmetros para configurar conexão com a impressora         |
| 2     | Abrir Conexão                 | Sistema se conecta com a impressora e permite realizar funções                |
| 3     | Imprimir Texto                | Digita o que quiser → imprime centralizado, negrito, fonte normal             |
| 4     | Imprimir QR Code              | Digita URL/texto → gera QR Code tamanho 6, correção alta                      |
| 5     | Imprimir Código de Barras     | Code128 com texto do usuário ou padrão {A012345678912}, mostra acima e abaixo |
| 6     | Imprimir XML SAT              | Imprime cupom SAT do arquivo XMLSAT.xml (já incluso para teste)               |
| 7     | Imprimir XML Cancelamento SAT | Imprime cancelamento com assinatura já preenchida                             |
| 8     | Abrir Gaveta Elgin            | Abre gaveta no pino Elgin (mais confiável)                                    |
| 9     | Abrir Gaveta padrão           | Abre gaveta genérica                                                          |
| 10    | Emitir Beep                   | 4 beeps rápidos – perfeito para chamar atenção                                |
| 11    | Obter Versão DLL              | Obtém versão do arquivo DLL instalado                                         |
| 0     | Fechar Conexão                | Fecha conexão com impressora e encerra o sistema                              |

## 🐰 Problemas que eu enfrentei (pra você não sofrer)

- Configurar o JNA pela primeira vez dá um medinho → solução: só adicionar os dois JARs no classpath
- Entender como funciona Interface + JNA → depois que pega o jeito vira mágica
- Documentação da Elgin é ótima, mas tem pouquíssimos exemplos em Java → por isso este projeto existe agora!

## 🔮 Próximos passos (sonhando alto)

- [ ] Transformar em GUI bonitona com botões, preview do cupom, seleção de arquivos etc.
- [ ] Suporte a mais modelos Elgin (i7, i8, etc.)
- [ ] Empacotar como .exe com Launch4j ou GraalVM native image
- [ ] Adicionar impressão de imagens e logos
- [ ] Modo "demo" que imprime um cupom completo automaticamente

## 💜 Feito com muito carinho por um dev que cansou de ficar montando string toda hora

Se esse projeto te ajudou nem que seja 5 minutos da sua vida, me dá uma estrelinha no GitHub que já fico feliz demais! ⭐

Qualquer dúvida, abre uma issue ou me chama que eu ajudo com prazer.

Boas impressões! 🖨️✨
## 👤 Autores
**Bruno Ranzoni, Davi Lima, Dhalessandro, Gustavo Barros, Issam Hassan, Ryan Alves**

<a href="https://github.com/dhalessandrods">
<img src="https://github.com/dhalessandrods.png" width="70" style="border-radius:50%">
</a>

Obrigado a todos que já deram estrela, reportaram bug ou só vieram aqui falar que o projeto salvou o dia! 💜
