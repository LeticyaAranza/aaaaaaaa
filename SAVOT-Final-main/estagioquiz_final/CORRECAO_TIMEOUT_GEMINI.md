# Correção da falha 504 do Gemini

- `chatbot/servico.py`: registra falhas da geração Gemini nos logs e retorna os links obtidos pelo Tavily quando houver erro ou resposta vazia. Não inventa uma resposta factual.
- `chatbot/views.py`: reconhece também `504` e `DEADLINE_EXCEEDED` no tratamento genérico de erros externos.
- Nenhuma chave foi adicionada ao projeto. Configure `TAVILY_API_KEY` e `GEMINI_API_KEY` em Render > Environment.
- `GEMINI_MODEL` é opcional e usa `gemini-2.5-flash` por padrão.
- A alteração não garante que a API Gemini deixe de retornar 504; garante que fontes recuperadas continuem disponíveis quando isso ocorrer.
- Após enviar ao GitHub, faça redeploy no Render e verifique os logs.
