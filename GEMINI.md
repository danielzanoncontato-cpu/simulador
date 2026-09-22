# DIRETRIZES E REGRAS MANDATÓRIAS: BDR - LEAD AI

## 🚨 REGRAS DE OURO INVIOLÁVEIS DO PROJETO

1. **AUDITORIA E CONTABILIZAÇÃO EM TEMPO DE EXECUÇÃO (ZERO HARDCODING):**
   - Antes de exibir, relatar ou renderizar QUALQUER número de leads ao usuário ou nos dashboards, o agente DEVE inspecionar e contabilizar programaticamente o número exato de registros no banco (`prospects.length` e linhas de `base_prospeccao_prx.csv`).
   - NUNCA assumir, estimar ou deixar valores fixos/estáticos no HTML, nos badges de cabeçalho (`compHeaderCount`), nos badges de abas (`tabProspectsBadge`) ou nos `<select>` de segmentos.
   - Todo componente visual DEVE ser alimentado pela função `updateDynamicCounts()` em JavaScript baseada no tamanho real do array `prospects`.

2. **RIGOR ABSOLUTO NA AUDITORIA LINHA POR LINHA (PORTUGUÊS, NOMES E CONFERÊNCIA COM SITE/REDES):**
   - O agente DEVE ter **rigor extremo e conferir linha por linha** de todos os registros minerados:
     - **Ortografia e Gramática em Português:** Verificar linha por linha se a linguagem, descrições de atividades, cargos, cidades, segmentos e scripts de abordagem estão em português 100% correto (acentuação, concordância e pontuação impecáveis).
     - **Nome por Nome (Sócios, Decisores e Empresas):** Conferir rigorosamente a grafia exata de cada nome de sócio e administrador do QSA oficial, bem como a Razão Social e Nome Fantasia da empresa, sem abreviações corrompidas ou erros de digitação.
     - **Conferência Rigorosa com Sites e Redes:** Validar cada informação com o site oficial da empresa, perfil verificado no LinkedIn, Google Meu Negócio / Maps e cadastros públicos na internet. Qualquer divergência deve ser saneada com base na verdade documental.

3. **MAPEAMENTO AMPLO DE MÚLTIPLOS CNAES POR ICP (PRINCIPAL & SECUNDÁRIOS):**
   - Cada segmento e ICP possui uma gama ampla de atividades correlatas. A mineração DEVE mapear e cobrir **todos os CNAEs possíveis** da cadeia (CNAE Principal + CNAEs Secundários de produção, logística, distribuição, comércio atacadista e serviços auxiliares).
   - Garantir que a base possua a lista completa de códigos CNAE para cruzamento e filtros avançados.

4. **VERIFICAÇÃO OBRIGATÓRIA EM FONTES OFICIAIS:**
   - Toda empresa minerada deve ser obrigatoriamente validada no tripé:
     - **Receita Federal / Juntas Comerciais:** CNPJ ativo, idade, CNAEs e QSA oficial com nomes de Sócios e Administradores.
     - **Google Meu Negócio / Maps / Web:** Validação de sede física, telefone comercial, site oficial institucional e porte.
     - **LinkedIn:** Perfis profissionais dos sócios/CEOs/CFOs do QSA e canais de contato direto.

5. **PROTOCOLO DE FALLBACK (SOLICITAÇÃO DE EXCEL EXPORTADO):**
   - Caso um nicho específico, base restrita ou segmento não possa ser minerado ou extraído automaticamente de fontes públicas, o agente DEVE **solicitar explicitamente ao usuário o envio de uma planilha Excel/CSV exportada** para que o sistema realize o enriquecimento, cruzamento societário e padronização nas 24 colunas.

6. **SINCRONIZAÇÃO BILATERAL COMPLETA E OBRIGATÓRIA:**
   - Sempre que houver mineração, adição, exclusão ou edição de leads, o agente DEVE atualizar automaticamente:
     1. **Locais Físicos do Computador:**
        - Área de Trabalho: `C:\Users\Daniel Zanon\Desktop\PRX Capital - Base de Prospeccao BDR`
        - Documentos: `C:\Users\Daniel Zanon\Documents\PRX Capital BDR`
        - Workspace Ativo Antigravity
        - Pacote Compactado: `PRX_Capital_BDR_Completo.zip` (Desktop e Documentos)
     2. **Nuvem e Repositório GitHub (GitHub Pages):**
        - Repositório: `https://github.com/danielzanoncontato-cpu/simulador`
        - Dashboard Online: `https://danielzanoncontato-cpu.github.io/simulador/`

7. **PADRÃO DAS 24 COLUNAS DE MINERAÇÃO E ENRIQUECIMENTO:**
   - Colunas obrigatórias: `ID, Empresa, CNPJ, Idade, UF, Cidade, Segmento, Cor_Segmento, Fonte_Dados, Setor, Tem_Site, Site, Descricao, CNAE_Principal, CNAE_Secundarios, Decisor_1_Nome, Decisor_1_Cargo, Decisor_1_LinkedIn, Decisor_1_Contato, Decisor_2_Nome, Decisor_2_Cargo, Decisor_2_LinkedIn, Decisor_2_Contato, Score_PRX`.
   - Codificação: UTF-8 com BOM para abertura sem falhas no Microsoft Excel.
   - Acesso 100% livre de senhas ou telas de login.

8. **MOTOR DE DISPARO AUTOMATIZADO EXCLUSIVO VIA RESEND (NUNCA GOOGLE/GMAIL):**
   - O sistema, dashboards e robôs DEVEM operar exclusivamente via integração **Resend API** (Chave de API ativa do projeto).
   - NUNCA perguntar, propor, sugerir ou solicitar senhas de aplicativo Google ou redirecionar a infraestrutura de disparo para fora do Resend. Todo disparo automatizado é processado pelo motor Resend.

9. **INTEGRAÇÃO DIRETA DE ABORDAGEM VIA RESEND API & WHATSAPP:**
   - Todo disparo direto e cópia de pitch executados pelo operador utilizam a infraestrutura Resend API e os links diretos do WhatsApp Web, sem intermediários ou telas de login.

10. **PADRÃO UNIFICADO E OFICIAL DE ABORDAGEM WHATSAPP E E-MAIL (PRIMEIRO CONTATO):**
    - Todo disparo, botão de envio no dashboard (`📲 WhatsApp`, `📋 Copiar Pitch`, modal de detalhes `openLeadModal`) e gerador de scripts DEVE utilizar estritamente o modelo de cópia oficial consultiva de alto impacto da PRX Capital, personalizando dinamicamente `{NOME}` (Decisor / Sócio):
      - **WhatsApp Oficial (Primeiro Contato):**
        ```text
        Olá, {NOME}! Tudo bem?

        Sou o Daniel Zanon, da PRX Capital (prxcapital.com.br).

        Atuamos como multi-family office e boutique financeira, assessorando empresários e famílias na gestão completa de suas estruturas físicas e jurídicas.

        Nossas frentes de atuação abrangem:
        * Gestão de carteiras e investimentos
        * Operações de câmbio e derivativos
        * Seguros patrimoniais
        * Créditos e financiamentos (capital de giro e antecipação de recebíveis)
        * Pesquisa e análise econômica (valuation e viabilidade financeira)
        * Revisão e planejamento patrimonial, tributário e sucessório

        O objetivo é blindar o capital, reduzir atritos fiscais e bancários e otimizar a tomada de decisão e a liquidez de seu patrimônio.

        Gostaria de agendar um diagnóstico inicial gratuito para melhorar a eficiência da sua estrutura empresarial ou familiar? (a conversa leva 15 minutos e pode ser ajustada nesta semana ou na próxima)

        Um abraço,
        Daniel Zanon | PRX Capital
        prxcapital.com.br
        ```
      - **E-mail Oficial (Primeiro Contato):**
        - **Assunto:** `Alinhamento estratégico & multi-family office | Daniel Zanon (PRX Capital)`
        - **Corpo:** Cópia idêntica de alto impacto com os 6 pilares centrais, chamada de diagnóstico e assinatura oficial de Daniel Zanon (`Daniel Zanon | Executivo de Negócios | PRX Capital | daniel@prxcapital.com.br`).

11. **PRESERVAÇÃO INTEGRAL DE TODOS OS SÓCIOS E DECISORES (PROIBIÇÃO DE DADOS SINTÉTICOS / FAKE):**
    - O sistema e o agente NUNCA devem inventar, simular proceduralmente ou substituir cadastros reais por dados artificiais/fictícios para inflar contagens.
    - Todos os sócios, diretores e conselheiros mapeados no QSA oficial da Receita Federal e Juntas Comerciais (ex: Castelo Alimentos com Marcelo Cereser, Valmir Cereser, Carlos Alberto Cereser, Maria Thereza Cereser, etc.) DEVEM ser preservados integralmente em cada empresa no array `decisores`, bem como todos os seus dados reais (telefones, e-mails corporativos, LinkedIn verificado e CNAEs).
    - Na tabela do dashboard e nos modais, TODOS os sócios e decisores de cada empresa devem ser exibidos de forma clara e acessível, com seus respectivos cargos e contatos diretos.

12. **IMUTABILIDADE ESTRUTURAL E BLINDAGEM CONTRA REGRESSÃO DA INTERFACE E DADOS:**
    - Toda alteração, nova funcionalidade, mineração de novos nichos ou ajuste de código DEVE preservar 100% da integridade da base existente e a arquitetura visual da interface.
    - É TERMINANTEMENTE PROIBIDO desconfigurar o layout visual (tema monocromático preto e branco puro, cabeçalho, tabela de 8 colunas, cards, modais e botões de ação), apagar/sobrescrever cadastros de leads anteriores ou corromper dados do QSA ao pesquisar novos leads ou anexar novas funções.
    - Minerações e pesquisas de novos leads DEVEM ser tratadas estritamente como adições incrementais sem modificar, truncar ou resetar os registros e a estrutura pré-existentes.
