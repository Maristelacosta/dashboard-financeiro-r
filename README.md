# ====================================================================
# PROJETO: Análise Financeira em R
# AUTORA: Maristela Costa[cite: 2]
# DESCRIÇÃO: Análise de receitas, despesas e lucros com estatística
# descritiva e visualização de dados financeiros.
# ====================================================================

# 1. Definição dos Vetores de Dados Mensais
meses <- c("Jan", "Fev", "Mar", "Abr", "Mai", "Jun")
receitas <- c(2000, 2500, 2200, 3000, 2800, 3500)
despesas <- c(1200, 1400, 1300, 1800, 1600, 2000)

# 2. Cálculo do Lucro Mensal
lucro <- receitas - despesas
print("Lucro mensal calculado:")
print(lucro)

# 3. Estatísticas Financeiras Gerais
receita_total <- sum(receitas)
despesa_total <- sum(despesas)
lucro_total <- sum(lucro)
receita_media <- mean(receitas)
margem_lucro_media <- mean(lucro / receitas) * 100

cat("\n--- Resumo Financeiro ---")
cat("\nReceita Total: R$", receita_total)
cat("\nDespesa Total: R$", despesa_total)
cat("\nLucro Total: R$", lucro_total)
cat("\nReceita Média Mensal: R$", round(receita_media, 2))
cat("\nMargem de Lucro Média: ", round(margem_lucro_media, 2), "%\n")

# 4. Estruturação dos Dados em Data Frame
dados_financeiros <- data.frame(
  Mes = meses,
  Receita = receitas,
  Despesa = despesas,
  Lucro = lucro
)

print("\nTabela Consolidada:")
print(dados_financeiros)

# 5. Visualização de Dados (Gráficos)
# Configurar uma janela gráfica para exibir vários gráficos lado a lado
par(mfrow = c(1, 3))

# Gráfico de Receitas Mensais
barplot(receitas, names.arg = meses, col = "forestgreen", 
        main = "Receitas Mensais", ylab = "R$", xlab = "Meses")

# Gráfico de Despesas Mensais
barplot(despesas, names.arg = meses, col = "firebrick", 
        main = "Despesas Mensais", ylab = "R$", xlab = "Meses")

# Gráfico de Tendência de Lucro
plot(lucro, type = "o", col = "dodgerblue", lwd = 2, 
     main = "Evolução do Lucro", xlab = "Meses", ylab = "Lucro (R$)", 
     xaxt = "n")
axis(1, at = 1:length(meses), labels = meses)
