# BDR - LEAD AI | DOCUMENTAÇÃO E CÓDIGO FONTE COMPLETO DO PROJETO

## 📌 1. Visão Geral do Sistema
O **BDR - LEAD AI** é uma plataforma avançada de inteligência de prospecção ativa, mineração e enriquecimento societário desenvolvida para a **PRX Capital** (Multi-family office & Boutique Financeira).

O sistema centraliza:
1. **Base Master Ativa de Prospecção:** Mais de 3.900 empresas de alto faturamento (High-Ticket AAA) com Quadro Societário Oficial (QSA), Sócios-Administradores, Diretores, Telefones, WhatsApps validados, E-mails corporativos, CNAEs Principal/Secundários e URLs institucionais verificadas.
2. **Classificação e Filtro Estrutural CNAE (IBGE / CONCLA Níveis 1 a 5):** Filtro inteligente de rolagem contendo todas as **21 Grandes Seções CNAE (Seções A a U)** cruzando com os códigos de divisão (01 a 99) e palavras-chave oficiais da Receita Federal e Juntas Comerciais.
3. **Motor de Mineração Inteligente:** Robô automatizado para identificação e enriquecimento de novos leads em 5 estados estratégicos (**São Paulo, Minas Gerais, Mato Grosso, Paraná e Santa Catarina**), com cruzamento documental rigoroso (Receita Federal, Juntas Comerciais, Google Maps e LinkedIn).
4. **Módulo de Abordagem Multicanal:** Integração direta com **WhatsApp Web** e infraestrutura de e-mail via **Resend API**, padronizados na cópia consultiva oficial de primeiro contato da PRX Capital.

---

## 🏛️ 2. Regras de Ouro e Conformidade Legal
- **Zero Hardcoding:** Toda contagem exibida na interface é calculada dinamicamente com base no tamanho real do array `prospects` (`updateDynamicCounts()`).
- **Rigor Documental e Ortográfico:** Verificação estrita linha por linha em português impecável, com grafia exata de sócios do QSA da Receita Federal e JUCESP/JUNTAS.
- **Conformidade Tributária (LC 123/2006):** Sociedades Anônimas (S/A) e Cooperativas são obrigatoriamente vinculadas a Lucro Real / Isenção (Ato Cooperativo), nunca ao Simples Nacional. O Simples Nacional é reservado exclusivamente a Sociedades Limitadas (LTDA), Sociedades Simples (S/S) e SLU elegíveis.
- **Padrão dos 5 Estados Autorizados:** Toda a filtragem e geração de novos cadastros opera exclusivamente em **SP, MG, MT, PR e SC**.

---

## 🏷️ 3. Estrutura de Grandes Seções CNAE (IBGE / CONCLA - Nível 1 a 5)

O filtro de segmentos (`#segmentFilter`) incorpora as 21 Grandes Seções da Classificação Nacional de Atividades Econômicas (CONCLA/IBGE):

| Seção | Divisões CNAE | Descrição da Grande Seção Econômica |
|---|---|---|
| **Seção A** | `01 a 03` | Agricultura, Pecuária, Produção Florestal, Pesca e Aqüicultura |
| **Seção B** | `05 a 09` | Indústrias Extrativas, Mineração, Gás e Petróleo |
| **Seção C** | `10 a 33` | Indústrias de Transformação, Fábricas e Manufatura |
| **Seção D** | `35` | Eletricidade, Gás e Energia |
| **Seção E** | `36 a 39` | Água, Esgoto, Gestão de Resíduos e Descontaminação |
| **Seção F** | `41 a 43` | Construção Civil, Engenharia, Edificações e Obras |
| **Seção G** | `45 a 47` | Comércio Atacadista, Varejista e Reparação de Veículos |
| **Seção H** | `49 a 53` | Transporte, Armazenagem, Cargas, Frotas e Correio |
| **Seção I** | `55 a 56` | Alojamento, Hotelaria e Alimentação (Restaurantes/Bares) |
| **Seção J** | `58 a 63` | Informação, Tecnologia, Telecomunicações e Software (SaaS) |
| **Seção K** | `64 a 66` | Atividades Financeiras, Seguros, Holdings e Previdência |
| **Seção L** | `68` | Atividades Imobiliárias, Loteamentos e Incorporação |
| **Seção M** | `69 a 75` | Atividades Profissionais, Científicas, Técnicas e Jurídicas |
| **Seção N** | `77 a 82` | Serviços Administrativos, Apoio e Terceirização |
| **Seção O** | `84` | Administração Pública, Defesa e Seguridade Social |
| **Seção P** | `85` | Educação, Ensino, Universidades e Escolas |
| **Seção Q** | `86 a 88` | Saúde Humana, Hospitais, Clínicas e Laboratórios |
| **Seção R** | `90 a 93` | Artes, Cultura, Esporte e Recreação |
| **Seção S** | `94 a 96` | Outras Atividades de Serviços, Associações e Sindicatos |
| **Seção T** | `97` | Serviços Domésticos |
| **Seção U** | `99` | Organismos Internacionais e Outras Instituições |

---

## 📊 4. Dicionário de Dados (Padrão Oficial das 24 Colunas)
Cada registro na base de prospecção e no arquivo CSV exportável segue a estrutura padronizada:

| # | Coluna | Descrição | Exemplo |
|---|---|---|---|
| 1 | `ID` | Identificador numérico sequencial | `1` |
| 2 | `Empresa` | Razão Social / Nome Fantasia | `Castelo Alimentos S/A` |
| 3 | `CNPJ` | Cadastro Nacional de Pessoa Jurídica | `07.814.284/0001-07` |
| 4 | `Idade` | Tempo de fundação e ano | `59 anos (1967)` |
| 5 | `UF` | Estado federativo da sede | `SP` |
| 6 | `Cidade` | Município da sede | `Jundiaí` |
| 7 | `Segmento` | Ramo de atividade econômica | `Fábricas & Indústrias` |
| 8 | `Cor_Segmento` | Identificador visual do ICP | `YELLOW` |
| 9 | `Fonte_Dados` | Órgão/Registro de validação | `JUCESP / Receita Federal + LinkedIn` |
| 10 | `Setor` | Classificação macroeconômica | `Indústria de Alimentos e Bebidas` |
| 11 | `Tem_Site` | Indicador de presença digital | `Sim` |
| 12 | `Site` | URL oficial do website | `https://www.casteloalimentos.com.br` |
| 13 | `Descricao` | Resumo institucional do negócio | `Líder no mercado de vinagres e condimentos...` |
| 14 | `CNAE_Principal` | Código CNAE principal com descrição | `1099-6/01 (Fabricação de vinagres)` |
| 15 | `CNAE_Secundarios` | Lista de CNAEs secundários | `1099-6/99, 1032-5/99, 4639-7/01, 5211-7/99` |
| 16 | `Decisor_1_Nome` | Nome do Sócio-Administrador principal | `Marcelo Cereser` |
| 17 | `Decisor_1_Cargo` | Cargo do primeiro decisor | `Diretor Superintendente / CEO` |
| 18 | `Decisor_1_LinkedIn`| URL do perfil profissional verificado | `https://www.linkedin.com/in/marcelo-cereser/` |
| 19 | `Decisor_1_Contato` | Telefone celular e e-mail direto | `(11) 94187-6309 / marcelo.cereser@...` |
| 20 | `Decisor_2_Nome` | Nome do segundo sócio/diretor | `Valmir Cereser` |
| 21 | `Decisor_2_Cargo` | Cargo do segundo decisor | `Diretor Industrial & Conselheiro` |
| 22 | `Decisor_2_LinkedIn`| LinkedIn do segundo decisor | `https://www.linkedin.com/...` |
| 23 | `Decisor_2_Contato` | Contato direto do segundo sócio | `(11) 4582-8000 / valmir.cereser@...` |
| 24 | `Score_PRX` | Classificação de ticket e aderência | `AAA (High-Ticket)` |

---

## 💬 5. Modelos Oficiais de Abordagem (Primeiro Contato PRX Capital)

### 📲 WhatsApp Oficial (Primeiro Contato):
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

### ✉️ E-mail Oficial (Primeiro Contato):
- **Assunto:** `Alinhamento estratégico & multi-family office | Daniel Zanon (PRX Capital)`
- **Remetente:** `Daniel Zanon | Executivo de Negócios | PRX Capital | daniel@prxcapital.com.br`

---

## 💻 6. Arquitetura de Código dos Módulos Principais

### A. Estrutura de Arquivos do Projeto:
- `index.html`: Dashboard Master Executivo com interface Tailwind CSS, suporte a tema claro/escuro, seletor de Grandes Seções CONCLA/IBGE, tabela paginada com link de site sob segmento, modal completo e abas ativas.
- `dashboard_prospeccao.html`, `bdr_dashboard_view.html`, `widget_prospeccao.html`: Espelhos sincronizados do dashboard para uso local ou embed.
- `prospects_database.json`: Banco de dados mestre com 3.900 empresas e quadros societários estruturados em formato JSON.
- `prospects_data.js`: Versão em JavaScript global do banco de dados para execução cliente autônoma.
- `base_prospeccao_prx.csv` / `base_prospeccao_prx_detalhada.csv`: Arquivos CSV oficiais com BOM UTF-8 para abertura direta no Microsoft Excel.
- `sync_prx.ps1`: Script PowerShell de sincronização bilateral com Área de Trabalho, Documentos e empacotamento ZIP.

### B. Mapeamento e Rastreio de Seções CONCLA / Receita Federal:
```javascript
var CONCLA_SECOES_MAP = {
  'CNAE_SEC_A': { divs: [1, 2, 3], keywords: ['agric', 'agro', 'soja', 'milho', 'cafe', 'pecuaria', 'gado', 'cana', 'florest', 'pesca', 'lavoura', 'graos'] },
  'CNAE_SEC_B': { divs: [5, 6, 7, 8, 9], keywords: ['miner', 'petroleo', 'gas', 'extrac', 'mineracao'] },
  'CNAE_SEC_C': { divs: [10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33], keywords: ['fabric', 'industr', 'manufat', 'alimento', 'bebida', 'textil', 'quimic', 'metalur', 'maquin', 'embalag', 'frigorifico'] },
  'CNAE_SEC_D': { divs: [35], keywords: ['energia', 'eletric', 'gas', 'solar', 'eolica', 'biomassa'] },
  'CNAE_SEC_E': { divs: [36, 37, 38, 39], keywords: ['agua', 'esgoto', 'residuo', 'descontam', 'recicla', 'saneam'] },
  'CNAE_SEC_F': { divs: [41, 42, 43], keywords: ['constru', 'edific', 'obra', 'incorpor', 'engenh', 'infraestrut'] },
  'CNAE_SEC_G': { divs: [45, 46, 47], keywords: ['comercio', 'atacado', 'varejo', 'distribui', 'represent', 'loja', 'importac', 'exportac', 'trading'] },
  'CNAE_SEC_H': { divs: [49, 50, 51, 52, 53], keywords: ['transp', 'logist', 'armaz', 'deposito', 'frot', 'aereo', 'carga', 'rodov', 'armaz'] },
  'CNAE_SEC_I': { divs: [55, 56], keywords: ['hotel', 'alojam', 'restaurante', 'alimenta', 'hospedag'] },
  'CNAE_SEC_J': { divs: [58, 59, 60, 61, 62, 63], keywords: ['softw', 'tecnol', 'comput', 'informac', 'telecom', 'dados', 'saas', 'comunicac', 'midia'] },
  'CNAE_SEC_K': { divs: [64, 65, 66], keywords: ['financ', 'banco', 'segur', 'cambio', 'invest', 'credito', 'holding', 'previd'] },
  'CNAE_SEC_L': { divs: [68], keywords: ['imobil', 'locac', 'loteam', 'imovel', 'corret'] },
  'CNAE_SEC_M': { divs: [69, 70, 71, 72, 73, 74, 75], keywords: ['advoc', 'jurid', 'contab', 'auditor', 'consult', 'engenhar', 'arquitet', 'publicid', 'market', 'pericia'] },
  'CNAE_SEC_N': { divs: [77, 78, 79, 80, 81, 82], keywords: ['locacao', 'terceir', 'limpeza', 'seguranca', 'cobranca', 'vigilanc'] },
  'CNAE_SEC_O': { divs: [84], keywords: ['administracao publica', 'defesa', 'seguridade'] },
  'CNAE_SEC_P': { divs: [85], keywords: ['educac', 'escola', 'ensino', 'faculd', 'univers', 'colegio'] },
  'CNAE_SEC_Q': { divs: [86, 87, 88], keywords: ['saude', 'medic', 'hospit', 'clinic', 'laborat', 'odont', 'cirurg', 'terapia'] },
  'CNAE_SEC_R': { divs: [90, 91, 92, 93], keywords: ['arte', 'cultura', 'esporte', 'recreac', 'lazer', 'academia'] },
  'CNAE_SEC_S': { divs: [94, 95, 96], keywords: ['associac', 'organizac', 'reparac', 'sindicato', 'culto'] },
  'CNAE_SEC_T': { divs: [97], keywords: ['servicos domesticos'] },
  'CNAE_SEC_U': { divs: [99], keywords: ['organismos internacionais', 'extraterritoriais'] }
};

function extractCnaeDivsJs(cnaeStr) {
  if (!cnaeStr) return [];
  var divs = [];
  var regex = /(\d{2})\d{2}-\d(?:\/\d{2})?/g;
  var match;
  while ((match = regex.exec(cnaeStr)) !== null) {
    divs.push(parseInt(match[1], 10));
  }
  var rawNums = cnaeStr.match(/\b\d{2}(?=\d{2}-|\d{2}\/)/g) || [];
  for (var i = 0; i < rawNums.length; i++) {
    divs.push(parseInt(rawNums[i], 10));
  }
  return divs;
}

function matchLeadToConclaSecao(p, secaoKey) {
  var secao = CONCLA_SECOES_MAP[secaoKey];
  if (!secao) return false;

  var leadDivs = extractCnaeDivsJs(p.cnaePrincipal).concat(extractCnaeDivsJs(p.cnaeSecundarios));
  for (var i = 0; i < leadDivs.length; i++) {
    if (secao.divs.indexOf(leadDivs[i]) !== -1) return true;
  }

  var haystack = normStr(
    (p.company || '') + ' ' +
    (p.segmentoNome || '') + ' ' +
    (p.setor || '') + ' ' +
    (p.desc || '') + ' ' +
    (p.cnaePrincipal || '') + ' ' +
    (p.cnaeSecundarios || '')
  );

  for (var j = 0; j < secao.keywords.length; j++) {
    if (haystack.indexOf(secao.keywords[j]) !== -1) return true;
  }

  return false;
}
```

---

## 🚀 7. Instruções de Execução e Deploy
1. **Abertura Local:** Executar o arquivo `Abrir Dashboard PRX.bat` ou abrir diretamente `index.html` em qualquer navegador web.
2. **Exportação:** Clicar nos botões de download para gerar a planilha formatada em CSV compatível com Microsoft Excel.
3. **Sincronização:** Todas as alterações são sincronizadas bilateralmente com a pasta `C:\Users\Daniel Zanon\Downloads\Códigos\Minerador`, a Área de Trabalho, os Documentos e o pacote `PRX_Capital_BDR_Completo.zip`.
