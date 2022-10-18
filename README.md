# comportamento

#O questionário utiliza uma Escala Tipo-Likert de sete pontos, onde 1 representa que o
respondente "Discorda totalmente" da proposição apresentada, e 7 representa, que o
respondente "Concorda totalmente”; os valores de dois a seis representam níveis de
concordância graduais e intermediários entre esses extremos.

#AJUSTE DOS DADOS
dados[ , 2:23] <- lapply(dados[ ,  2:23], function(x){ factor(x, 
                                                           levels = c("1", "2", "3", "4", "5","6", "7"),                                  
                                                           labels = c("Disc.total", "Disc.em Gr.", "Disc.parcial", "Nem, Nem", "Conc.parcial","Conc.em Gr.", "Conc.total"))})

names(dados)[ 2:23] <- paste(names(dados)[ 2:23], itens$texto, sep="_")


#install.packages("likert")
library(likert)
lik <- likert(as.data.frame(dados[ ,  2:23]))
title <- "Comportamento e valores do Usuario"
# Opção 1
plot(lik, wrap = 60, text.size=3) + theme(axis.text.y = element_text(size="5"))

# Opção 2
plot(lik, type = "heat", wrap = 60, text.size=3) + theme(axis.text.y = element_text( size="5"))
