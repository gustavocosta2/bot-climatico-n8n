# Bot de Previsão do Tempo Diária 🌤️

**Objetivo:** O objetivo da criação desse bot é para uma empresa onde os funcionários do departamento de marketing possam promover eventos ao ar livre, por exemplo dinâmicas em grupos e afins, sem precisar realizar cotidianamente a busca pelas informações do clima do dia. A proposta é que haja uma 
comunicação automática via email, slack ou outros meios de comunicação utilizados na empresa para as pessoas responsáveis pelas organizações desses eventos possuírem a informação rapidamente e automaticamente.

Ademais, o bot conta com a utilização de um modelo LLM para analisar os dados atmosféricos e informar a equipe de marketing se os dados são ou não favoráveis à realização de um evento.

****

## Metodologia

A metodologia para esse projeto foi bem intuitiva, o primeiro passo consistiu em realizar um fluxograma para formular como seria a automação à ser desenvolvida. A construção desse fluxograma foi feito utilizando o quadro branco do Canva para fazer o Brainstorm da automação.

- *Scheduling:* O scheduling foi colocado como a função de disparar o trigger. Todos os dias às 8h30min da manhã a automação é ativada. Isso deve-se ao fato do funcionário de marketing tender a consultar seu e-mail para saber quais serão seus compromissos do dia e como se planejar para eles.

- *API do Clima:* Para conseguir obter os dados do clima como temperatura mínima, temperatura máxima, a temperatura atual, umidade, velocidade do vento, etc. é necessário extrair esses dados de algum lugar que os disponibiliza. Para esse caso, foi utilizada a API do OpenWeatherMap que oferece
esses dados de forma gratuita e disponibiliza a documentação necessária para integrar a API no n8n.

- *Seleção de Features:* Essa etapa consiste em uma breve extração de dados fundamentais para o problema. A API traz consigo diversos dados meteorológicos e para uma análise simples se é viável ou não realizar um evento existem alguns dados que não são importantes para o contexto do problema,
por exemplo a pressão atmosférica que foi descartada entre outras. Assim, foi extraído apenas temperatura atual, a temperatura mínima e máxima, umidade e a velocidade do vento em metros por segundo.

- *IA:* Aqui, foi utilizado uma LLM para receber os dados meteorológicos do passo anterior e interpretá-los para informar o departamento de marketing. O modelo LLM utilizado foi o LLama com 70 bilhões de parâmetros versátil. Para mais, eu utilizei a técnica RICEE (Role, Instructions, Context, Example,
Especific) que consiste em utilizar um formato de prompt de formato .xml para instruir e adequar o modelo à um comportamento adequado evitando que aconteça uma alucinação do modelo, isto é, ele fuja do escopo ao qual ele foi definido: nesse caso, o modelo está restrito no contexto de ser um assistente
de previsão do tempo.

- *Slack/Gmail:* O último passo do fluxograma consiste em enviar o texto gerado pela IA em um canal de comunicação qualquer que a empresa utilize (whatsapp, slack, telegram, gmail, etc). Nesse projeto foi utilizado o gmail, todos os dias os funcionários do departamento de marketing receberão um
email conciso e objetivo sobre o clima do dia.

Nesse caso, o bot foi nomeado como sendo Kyle e trabalhando para uma empresa fictícia chamada de CostaCore que presta consultoria de dados e IA e realiza eventos com seus funcionários em certas ocasiões quando o clima é favorável.
