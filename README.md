## **Automação de charadas para TikTok**

## **Integrantes**

* Kaique Alves  
* Pedro Henrique  

## **Link do front-end (Replit)**:
https://replit.com/@kaiquead13/Charadinhas?v=1

---

## **Apresentação do Problema**

Atualmente, é muito comum que pessoas tentem criar páginas ou perfis em redes sociais como TikTok e YouTube Shorts com o objetivo de alcançar visibilidade e, eventualmente, gerar algum retorno financeiro. No entanto, para que isso seja minimamente viável, é necessário manter uma frequência alta de postagens, geralmente diária.

Essa exigência de constância torna-se um grande desafio para a maioria das pessoas, especialmente aquelas que precisam conciliar a criação de conteúdo com trabalho, estudos ou outras responsabilidades. A falta de tempo acaba sendo um dos principais fatores que impedem a continuidade e o crescimento desses projetos.

Diante desse cenário, surge a necessidade de soluções automatizadas que auxiliem na criação de conteúdo, reduzindo o esforço manual e permitindo maior regularidade nas publicações.

---

## **Solução Proposta**

Como solução para o problema apresentado, foi desenvolvida uma automação utilizando a ferramenta **n8n**, com o objetivo de automatizar a criação de charadas e gerar imagens a partir dessas charadas para serem utilizadas em postagens em redes sociais.

Além da automação, foi criado um front-end simples utilizando **vibe coding no Replit**, permitindo que o usuário interaja facilmente com o sistema e obtenha os resultados prontos para publicação.

O funcionamento da solução ocorre da seguinte forma:

1. O front-end realiza uma requisição para a automação no n8n por meio de um **Webhook**.

2. O Webhook aciona um **AI Agent**, configurado para se comunicar com uma LLM fornecida pela plataforma **GROQ**, solicitando a criação de uma charada.

3. A resposta gerada pela LLM é processada por um **nó de código**, onde o conteúdo é organizado em formato JSON.

4. Esse JSON é então utilizado para realizar uma requisição à **API do Hugging Face**, que gera uma imagem em formato PNG utilizando o modelo **FLUX.1-dev**.

5. A imagem gerada é processada por outro **nó de código**, responsável por converter o arquivo PNG em **base64**, facilitando o envio e a exibição no front-end.

6. Por fim, o nó **Respond to Webhook** é acionado, retornando ao front-end a charada, sua resposta e a imagem em base64.

7. No front-end, o usuário pode visualizar a charada, copiar os textos gerados e salvar a imagem para publicação em redes sociais.

---

## **Automação e resultados**

**Automação no n8n:**

<img width="1537" height="499" alt="fluxon8n" src="https://github.com/user-attachments/assets/e36b4b0d-9f83-4237-bb20-d2b88d6b3fd6" />

## 

**Fluxo feliz com front-end após receber a charada e a imagem do n8n:**

<img width="400" height="681" alt="n8nPrimeiraCharadaCompleta" src="https://github.com/user-attachments/assets/cf591944-2c7d-46c5-9dbc-fd1f050a92b9" />  

---

**Resultado ruim de imagens geradas com o conteúdo não fazendo sentido:**

<img width="700" height="700" alt="n8n1" src="https://github.com/user-attachments/assets/0ba29c7e-70b6-486f-b765-67e75878a02b" />
<img width="700" height="700" alt="n8n2" src="https://github.com/user-attachments/assets/8c2de4ac-0f65-4220-9e2e-790d8aeade40" />
<img width="700" height="700" alt="n8n5" src="https://github.com/user-attachments/assets/4a5c387f-f630-4392-bbe3-b24d0a890f61" />
<img width="700" height="700" alt="n8n3" src="https://github.com/user-attachments/assets/4e430b87-acb5-4e97-a97e-1cb8bf595e31" />
<img width="700" height="700" alt="n8n4" src="https://github.com/user-attachments/assets/575f9175-acfd-4c02-95c2-94ddbfb922ff" />

---

## **Problemas Encontrados**

Durante o desenvolvimento do projeto, alguns desafios foram identificados:

* As APIs de geração de imagens apresentam dificuldades em representar textos de forma totalmente fiel, frequentemente cometendo erros de gramática, pontuação ou até mesmo omitindo partes do texto solicitado.

* Houve dificuldade em encontrar serviços gratuitos para geração de imagens, e quando encontrados, os limites de uso eram atingidos rapidamente.

* Em alguns casos, as charadas geradas não apresentavam lógica ou acabavam se repetindo.

* Para a criação do front-end utilizando vibe coding, foi necessário utilizar créditos da plataforma Replit. Os créditos gratuitos disponíveis para testes são limitados e, em geral, se esgotam rapidamente. No caso deste projeto, o front-end foi finalizado na última interação gratuita disponível; caso contrário, seria necessário criar uma nova conta para continuar os testes.

---

## **Próximos passos e melhorias futuras**

Apesar de a automação cumprir o objetivo proposto que seria criar uma imagem, existem grandes melhorias relacionadas à **qualidade do conteúdo gerado nas imagens**. Como observado durante os testes, os modelos de geração de imagem apresentam dificuldades em representar textos longos de forma fiel, frequentemente cometendo erros de ortografia, pontuação ou posicionamento do texto. Para mitigar esse problema, um próximo passo seria **refinar os prompts enviados à API de geração de imagens**, tornando-os mais específicos, restritivos e adaptados às limitações do modelo utilizado.

Além disso, poderiam ser implementados **mecanismos de validação e controle de qualidade**, como:

* Verificação automática para evitar charadas repetidas;  
* Avaliação da coerência lógica das charadas geradas;  
* Ajustes dinâmicos no prompt conforme falhas identificadas em execuções anteriores.

Como evolução da automação, também seria possível adicionar:

* Agendamento automático de postagens em redes sociais;  
* Armazenamento das charadas e imagens geradas em um banco de dados;  
* Histórico de conteúdos já publicados;  
* Autenticação e controle de acesso ao Webhook.
