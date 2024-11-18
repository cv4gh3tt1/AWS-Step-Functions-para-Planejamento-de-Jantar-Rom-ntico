### Projeto: **AWS Step Functions para Planejamento de Jantar Romântico**

Este projeto implementa uma **AWS Step Functions** utilizando o modelo **Bedrock** para criar uma cadeia automatizada de prompts e respostas. O fluxo ajuda a planejar um jantar romântico, fornecendo ideias de combinações de pratos, bebidas e locais. 

---

#### **Objetivo**
Automatizar a interação com modelos de IA para gerar sugestões contextuais relacionadas a:
1. **Combinações gastronômicas** (acompanhamentos para um prato principal).
2. **Bebidas** que complementem o jantar.
3. **Locais ideais** para um jantar romântico.

---

#### **Fluxo do Step Functions**

1. **Pergunta ideias de combinação**  
   - Solicita sugestões de acompanhamentos para "macarrão com queijo" em um contexto de jantar romântico.  
   - Modelo utilizado: **Claude 3 (Anthropic)**.  
   - Armazena a resposta como `result_one`.

2. **Add first result to conversation history**  
   - Combina a sugestão inicial com o prompt original para formar o histórico da conversa.  
   - Prepara o histórico para o próximo passo.

3. **Ideias de bebidas**  
   - Solicita sugestões de duas bebidas (com estilos, safras ou variações) que combinem com o jantar.  
   - Modelo utilizado: **Claude 3 (Anthropic)**.  
   - Armazena a resposta como `result_two`.

4. **Add second result to conversation history**  
   - Atualiza o histórico da conversa, unindo as sugestões de acompanhamentos e bebidas.

5. **Ideias de lugares**  
   - Solicita a indicação de um lugar perfeito para um jantar romântico em Paris.  
   - Modelo utilizado: **Claude 3 (Anthropic)**.  
   - Finaliza o fluxo com a resposta armazenada como `result_three`.

---

#### **Estrutura do Arquivo JSON**
- **`States`**:
  - Define os estados (passos) do fluxo, cada um representando uma tarefa, como gerar um prompt ou atualizar o histórico.
- **`Parameters`**:
  - Configura o modelo Bedrock, incluindo:
    - ID do modelo.
    - Parâmetros do prompt (`Body`, `messages`, `max_tokens`).
  - Resultados de cada tarefa são armazenados com `ResultSelector` e combinados no histórico com `Pass`.
- **`End`**:
  - O estado final conclui o fluxo após sugerir o local.

---

#### **Exemplo de Uso**
O projeto é ideal para experimentos de **chaining prompts** e automação de recomendações personalizadas utilizando IA. Pode ser adaptado para outros contextos, como:
- Planejamento de eventos.
- Sugestões gastronômicas dinâmicas.
- Recomendações de experiências personalizadas.

---

#### **Requisitos**
1. **AWS Bedrock**: Acesso ao modelo Claude 3 (Anthropic).  
2. **AWS Step Functions** configuradas com permissões para acessar os modelos.  
3. Familiaridade com JSON para editar e expandir o fluxo.

---

#### **Como usar**
1. Faça upload do arquivo JSON no console do **AWS Step Functions**.
2. Configure as permissões para acessar **AWS Bedrock**.
3. Inicie o fluxo para receber sugestões automatizadas.

#### Projeto gerado com auxilio de IA ; )