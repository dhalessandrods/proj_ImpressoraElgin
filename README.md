<a>
<img src="https://softkore.com.br/wp-content/uploads/2020/09/Arte-para-Capa-Chamada-de-maetia-no-Blog-Review-de-Impressoras-Elgin.png" width="500" style="border-radius:1%" align="center">
</a>

# 🖨️ Sistema CLI Impressora Elgin i9
**Controlador por Linha de Comando (CLI) super amigável para Impressora Térmica Elgin i9 (via DLL)**

Um programa em Java puro que transforma as funções da DLL oficial da Elgin i9 num menu simples, intuitivo e extremamente fácil de usar.  
Perfeito para quem quer testar todas as funções da impressora (texto, QR code, código de barras, XML SAT, gaveta, beep, etc.) sem precisar escrever uma linha de código toda vez.
****
> “Finalmente consigo fazer a impressora fazer tudo que eu quero só digitando números!”  
> — Você, daqui a 2 minutos

## 🎯 Objetivo do projeto
Criar a forma **mais simples e humana possível** de interagir com todas as funções da impressora térmica Elgin i9 usando a DLL oficial, sem precisar montar strings complicadas ou lembrar parâmetros toda hora.

O foco é ser **rápido de aprender**, mesmo para quem nunca programou na vida. Basta abrir, escolher o número da função e testar na hora.

## 🛠️ Tecnologias utilizadas
- **Java 21+** (100% puro, sem frameworks)
- **JNA** (Java Native Access) – para carregar e usar a DLL da Elgin
- **Documentação Elgin**: Utilizado como auxílio para desenvolver o programa (https://elgindevelopercommunity.github.io/group___m1.html) 

## 📦 Dependências necessárias
- **JNA** → `jna-5.15.0.jar` + `jna-platform-5.15.0.jar` (já incluídos no repositório ou baixe em https://github.com/java-native-access/jna)
- **DLL da Elgin** → `E1_Impressora01.dll` (vem com o driver oficial da i9 – versão testada: 01.12.11)
****
## 🚀 Como executar (passo a passo ridiculamente simples)
*Siga exatamente esses passos, um de cada vez. Não pule nada, mesmo que pareça bobo. Tudo foi testado várias vezes para ficar o mais fácil possível.*

### 1. Baixe o programa completo (é só clicar)
Acesse este link do GitHub:  
👉 https://github.com/dhalessandrods/proj_ImpressoraElgin.git

Clique no arquivo que termina com **.zip** (exemplo: `proj_ImpressoraElgin-main`)  
→ O Windows vai baixar automaticamente para a pasta **Downloads** do seu computador

### 2. Descompacte a pasta (é só dar 2 cliques)
- Abra a pasta **Downloads**
- Dê dois cliques rápidos no arquivo `.zip` que você baixou
- Vai abrir uma janela mostrando uma pasta com nome parecido com “proj_ImpressoraElgin-main”
- Arraste essa pasta para a **Área de Trabalho** (ou para qualquer lugar que você quiser)
- Pode deletar o .zip depois, não vai precisar mais

### 3. Configurando o IntelliJ, programa para EXECUTAR o sistema da impressora
*Atenção: Recomendamos que use o IntelliJ como IDE para testes do sistema. NÃO USE outras.*
1. Abra o site https://www.jetbrains.com/pt-br/idea/download/download-thanks.html e instale o IntelliJ Community Edition
2. Instale a SDK do JAVA 24 dentro do IntelliJ CE
3. Importe a pasta 'proj_ImpressoraElgin-main' como projeto Java dentro do IntelliJ CE
4. Procure a pasta onde o arquivo `E1_Impressora01.dll` está baixado e copie o diretório. Será algo como:
   ```java 
   "C:\\SEU_CAMINHO\\Downloads\\proj_ImpressoraElgin-main\\E1_Impressora01.dll"
   ```
5. Procure o arquivo Main.java, que está dentro da pasta `src` e se prepare para editá-lo
6. Altere a linha do código (linha ~25) para o caminho correto da sua DLL:
   ```java
   Native.load("C:\\SEU_CAMINHO\\Downloads\\proj_ImpressoraElgin-main\\E1_Impressora01.dll", ImpressoraDLL.class);
   ```

7. Assim como no passo 5, copie o diretório da pasta onde está o está os arquivos `XMLSAT.xml` e `CANC_SAT.xml'
   Altere a linha do código (linha ~170) para o caminho correto do arquivo XMLSAT.xml
   ```java
   String dados = "path=C:\\SEU_CAMINHO\\Downloads\\proj_ImpressoraElgin-main\\XML_SAT.xml";
   ```
   
   Altere a linha do código (linha ~190) para o caminho correto do arquivo CANC_SAT.xml
   ```java
   String dados = "path=C:\\SEU_CAMINHO\\Downloads\\proj_ImpressoraElgin-main\\CANC_SAT.xml";
   ```

8. Agora é hora de configurar a BIBLIOTECA JNA para permitir que o código funcione bem:
- Acesse as *Configurações (ou Settings)*, engrenagem no canto superior direito do IntelliJ
- Procure por *Estrutura do projeto (ou Project Structure)*
- Depois *Biblioteca (ou libraries)*
- Clique em *+*, vá na pasta
   ```java
     >"C:\\SEU_CAMINHO\\Downloads\\proj_ImpressoraElgin-main\\libs"
   ```
  procure o arquivo `jna-5.15.0.jar`, clique em *de Java (ou from Java)*
- depois em *Abrir (ou open)* e, finalmente, em *Aplicar (ou apply)*

9. Pronto! Você já instalou o IntelliJ, corrigiu os diretórios e ainda instalou a biblioteca JNA.

**Agora você pode aproveitar todos os recursos do sistema ao máximo!**

> Dica de ouro: deixe os arquivos dentro da pasta do projeto e use caminho relativo:
> ```java
> Native.load("E1_Impressora01.dll", ImpressoraDLL.class);
> ```

### 4. Instalando o driver da Impressora Elgin i9
Se você ainda não tem:
1. Baixe o driver oficial da Elgin i9 aqui: https://elgin.com.br/suporte-tecnico/downloads
2. Ligue a impressora Elgin i9 na tomada
3. Conecte o cabo USB no computador (use a mesma porta USB de sempre)
4. Abra o arquivo de instalação do driver da impressora Elgin i9
5. Faça a instalação do driver
6. Depois de instalado, espere o Windows fazer barulhinho de “conectou” (uns 5-10 segundos)

Pronto! Agora a impressora e o programa estão configurados!.

### 5. Hora de testar!
1. Dentro do IntelliJ, com o arquivo Main.java selecionado, aperte as teclas de atalho ``ctrl + shift + F10``
2. Esse comando vai executar o arquivo. Vai aparecer uma tela com o menu do sistema. Seja bem-vindo!

## 📟 Menu principal (o que você vai ver na tela)****

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

### Testando o programa
Vai aparecer o menu grandão com os números de 0 a 11. Agora é só digitar o número da função que você quer e dar `Enter`

**Atenção:**

>Antes de começar a se divertir, faça uma configuração do sistema com o comando `1 - Configurar conexão`\
> Para fazer a configuração, basta colocar o que o programa mostra\
> Depois abra uma conexão do sistema com a impressora através do comando `2 - Abrir conexão`

Exemplo para imprimir um texto simples:
1. Digite `3` e aperte Enter (impressão de texto)
2. Digite o que você quer imprimir (ex: “Olá mundo!”) e aperte Enter
3. A impressora vai imprimir, avançar e cortar o papel automaticamente!

Caso haja um problema de execução: execute o comando `ctrl + shift + F10` novamente!

Para fechar o sistema, basta clicar em `0 - Fechar Conexão e Sair`

Todas as funções já avançam o papel e cortam automaticamente após imprimir.  
Você literalmente só digita o número e o texto quando solicitado.

## ⚙️ Funcionalidades já implementadas e testadas

| Opção | Função                        | O que acontece                                                        |
|-------|-------------------------------|-----------------------------------------------------------------------|
| 1     | Configurar Conexão            | Usuário digita os parâmetros para configurar conexão com a impressora |
| 2     | Abrir Conexão                 | Sistema se conecta com a impressora e permite realizar funções        |
| 3     | Imprimir Texto                | Digita o que quiser → imprime centralizado, negrito, fonte normal     |
| 4     | Imprimir QR Code              | Digita URL/texto → gera QR Code tamanho 6, correção alta              |
| 5     | Imprimir Código de Barras     | Code128 com texto padrão {A012345678912}, mostra acima e abaixo       |
| 6     | Imprimir XML SAT              | Imprime cupom SAT do arquivo XMLSAT.xml (já incluso para teste)       |
| 7     | Imprimir XML Cancelamento SAT | Imprime cancelamento com assinatura já preenchida                     |
| 8     | Abrir Gaveta Elgin            | Abre gaveta no pino Elgin (mais confiável)                            |
| 9     | Abrir Gaveta padrão           | Abre gaveta genérica                                                  |
| 10    | Emitir Beep                   | 4 beeps rápidos – perfeito para chamar atenção                        |
| 11    | Obter Versão DLL              | Obtém versão do arquivo DLL instalado                                 |
| 0     | Fechar Conexão e Sair         | Fecha conexão com impressora e encerra o sistema                      |

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
### Bruno Ranzoni, Davi Lima, Dhalessandro, Gustavo Barros, Issam Hassan, Ryan Alves

<a href="https://github.com/dhalessandrods">
<img src="https://github.com/dhalessandrods.png" width="70" style="border-radius:50%">
</a>

Obrigado a todos que já deram estrela, reportaram bug ou só vieram aqui falar que o projeto salvou o dia! 💜