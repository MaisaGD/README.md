# 📚 Caderno Temático: Engenharia de Prompts e Segurança em LLMs

> **Projeto Prático - Bootcamp DIO.me**  
> *Estudo prático sobre Inteligência Artificial, ancoragem de dados (Grounding), arquitetura RAG e Engenharia de Prompts utilizando o Google NotebookLM.*

---

## 🎯 Contexto e Objetivos

* **Tema Escolhido:** Engenharia de Prompts, Ancoragem e Riscos de Segurança em Aplicações de LLM.
* **Objetivos de Estudo:**
  1. Explorar o **Google NotebookLM** como assistente de aprendizagem ativa baseado em arquitetura **RAG** (*Retrieval-Augmented Generation*).
  2. Testar e documentar o refinamento de prompts para extração de conhecimento preciso e auditável.
  3. Mapear o comportamento da IA diante de limitações das fontes e registrar os ajustes de rota (*troubleshooting* e "cicatrizes").

---

## 📑 Curadoria de Fontes

Para compor a base de conhecimento do NotebookLM, foram adicionadas 3 fontes abertas de referência:

1. 📄 **[Prompt Engineering Guide (DAIR.AI)](https://www.promptingguide.ai/pt)** — Guia com conceitos fundamentais, técnicas e padrões de encadeamento de prompts.
2. 📄 **[Documentação Oficial do Google NotebookLM](https://support.google.com/notebooklm)** — Visão geral sobre funcionalidades, gestão de fontes e citações.
3. 📄 **[OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)** — Documento sobre vulnerabilidades críticas em LLMs, como *Prompt Injection* e *Overreliance*.

---

## 🧪 Engenharia de Prompts e "Cicatrizes" (Troubleshooting Real)

Esta seção registra como o refinamento dos prompts permitiu contornar respostas genéricas e limitações nas fontes originais.

### 🔴 Cicatriz 1: Limitação da Fonte e Pivotação Estratégica
* **Prompt Aplicado:**  
  > `"Monte uma tabela comparando os conceitos [Conceito A] e [Conceito B] com base nas fontes, listando: Definição, Vantagens, Desvantagens e Casos de Uso."`
* **Dificuldade Encontrada:**  
  Ao tentar comparar as técnicas *Zero-Shot* e *Few-Shot*, o NotebookLM apontou que o documento da DAIR.AI carregado continha apenas o menu de navegação, sem o texto explicativo detalhado dessas técnicas.
* **Solução / Ajuste:**  
  Em vez de forçar a IA a inventar dados (alucinar), o prompt foi ajustado para focar nas fontes com conteúdo completo. A comparação foi pivotada para dois conceitos críticos do documento OWASP: **Injeção de Prompt (LLM01)** vs. **Dependência Excessiva (LLM09)**.

---

### 🔴 Cicatriz 2: Refinamento para Ancoragem Estrita (Grounding)
* **Prompt Inicial:**  
  > `"O que é engenharia de prompts e quais são as principais técnicas?"`
* **Resultado Inicial:**  
  Resposta genérica que não utilizava todo o potencial de citação das fontes.
* **Prompt Refinado:**  
  > `"Com base EXCLUSIVAMENTE nas fontes fornecidas, defina Engenharia de Prompts e monte uma lista comparativa indicando quais técnicas avançadas são mencionadas nos textos. Indique o documento de origem para cada uma."`
* **Aprendizado:**  
  Instruções explícitas de exclusividade e solicitação de indicação da fonte ativam o mecanismo de ancoragem e citações do NotebookLM com precisão.

---

## 📖 Miniguia de Estudo (Entrega Final)

### 📊 Tabela Comparativa de Vulnerabilidades (OWASP LLM)

| Critério | Injeção de Prompt (LLM01) | Dependência Excessiva (LLM09) |
| :--- | :--- | :--- |
| **Definição** | Manipulação do modelo através do envio de entradas de texto maliciosas (*crafted inputs*). | Falha humana em aceitar cegamente as respostas do modelo sem validação crítica. |
| **Principais Riscos** | Burlar filtros de segurança, vazamento de dados e execuções não autorizadas. | Aceitação de alucinações/erros, gerando falhas operacionais e jurídicas. |
| **Foco de Mitigação** | Criação de filtros de entrada e sanitização rigorosa de prompts. | Implementação de supervisão humana (*human-in-the-loop*) e auditorias. |
| **Casos de Uso / Cenários** | *Jailbreaking* ou tentativas de extração das instruções do sistema (*Prompt Leaking*). | Aceitar automaticamente códigos ou relatórios gerados pela IA sem testes prévios. |

---

### 👥 Atuação na Engenharia de Prompts: Pesquisadores vs. Desenvolvedores

Segundo as fontes analisadas, o objetivo da engenharia de prompts varia conforme o perfil do profissional:

* **Pesquisadores:** Focam em explorar limites científicos dos modelos, aprimorando a capacidade dos LLMs em resolver tarefas lógicas complexas (raciocínio aritmético e QA).
* **Desenvolvedores:** Focam na aplicação prática, projetando instruções robustas que conectam LLMs a bancos de dados, APIs e ferramentas externas.

---

## 🔄 Prompts Reutilizáveis para Estudos

* 🎓 **Para Delimitação de Personas:**
  > `"Atue como um especialista em IA. Analise as fontes e identifique os 5 conceitos técnicos mais importantes sobre [Tema]. Para cada conceito forneça: Nome, Definição objetiva e Exemplo prático."`

* 📋 **Para Síntese Executiva:**
  > `"Resuma os 3 pontos centrais dos documentos carregados em formato de bullet points, destacando o impacto prático de cada um."`

* ❓ **Para Autoavaliação:**
  > `"Crie 5 perguntas de múltipla escolha para testar meu conhecimento sobre os documentos anexados. Não mostre a resposta imediatamente; aguarde eu responder para dar o gabarito."`

---

## 🛠️ Ferramentas Utilizadas
* **[Google NotebookLM](https://notebooklm.google.com/)** — Curadoria e estudo ancorado em fontes (RAG).
* **[GitHub](https://github.com)** — Documentação do projeto e portfólio.
* **Markdown** — Estruturação do repositório.
