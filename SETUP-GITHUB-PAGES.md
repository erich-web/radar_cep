# 🎯 CEO Radar - Setup

## ⚡ Quick Start

### 1. Criar Tabela no Supabase

Acesse: https://supabase.com/dashboard

1. Vá para **SQL Editor**
2. Execute este SQL:

\`\`\`sql
CREATE TABLE IF NOT EXISTS topics (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id TEXT NOT NULL,
  title TEXT NOT NULL,
  urgency INTEGER NOT NULL CHECK (urgency >= 1 AND urgency <= 5),
  importance INTEGER NOT NULL CHECK (importance >= 1 AND importance <= 5),
  status TEXT NOT NULL DEFAULT 'active' CHECK (status IN ('active', 'hold', 'completed')),
  created_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX IF NOT EXISTS idx_topics_user_id ON topics(user_id);

ALTER TABLE topics ENABLE ROW LEVEL SECURITY;

CREATE POLICY "Todos podem ler" ON topics FOR SELECT USING (true);
CREATE POLICY "Todos podem inserir" ON topics FOR INSERT WITH CHECK (true);
CREATE POLICY "Todos podem atualizar" ON topics FOR UPDATE USING (true) WITH CHECK (true);
CREATE POLICY "Todos podem deletar" ON topics FOR DELETE USING (true);
\`\`\`

### 2. Cadastrar Dados

1. Abra **setup-dados.html**
2. Clique em **INICIAR SETUP**
3. Aguarde completar

### 3. Visualizar Radar

1. Abra **index.html**
2. Clique no botão ☰ para ver seus assuntos

## 📊 Seus Assuntos

- 🔴 Fechar contrato Campari (U5 I5)
- 🟠 Fechar contrato Ambev (U4 I5)
- 🟡 Aprovar redução de folha (U3 I5)
- 🟠 Fechar consultora AI (U4 I4)
- 🟡 Finalizar plano de expansão (U3 I4)
- 🟢 Enviar kits copa (U2 I3)
