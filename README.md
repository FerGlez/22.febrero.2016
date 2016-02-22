# 22.febrero.2016
sdem215<-read.dbf("C:\\Users\\SALA-C30\\Downloads\\SDEMT215.dbf")
sdem215<-data.frame(sdem215)#### hacemos la base de datos data frame
help(str)
str(sdem215)
attach(sdem215)
table(SEX)
table(EDA)

EDA1<-as.numeric(as.character(EDA))## Para cambia a numerico
table(EDA1)


###### Ponderar casos #####
install.packages("questionr")### Van entre comillas 
require(questionr)
c0<-table(sdem215$SEX)
c0
c1<-wtd.table(sdem215$CLASE1,weights=sdem215$FAC)###
table(c1)
write.csv(c1,file='')### write es para exportar se puede guardar con la extension csv y lo puedes abrir en excel mor
c1
#Obtiene la tabla expandida con las nuevas etiquetas de CLASE1. EMplea la variable FAc (FActor de expansión)
# Se asigna a una variable para poder exportar

################Porcentajes######

tabrama<-wtd.table(sdem215$CLASE1,weights=sdem215$FAC)
c1.1<-round((tabrama/margin.table(tabrama))*100,2)## round es para redondear.
          ### tabrama suma cada uno de las casillas, el dos es para indicar el # de decimales
c1.1


##########Ocupados y no ocupados#####

sdem215$SEX<-ordered(sdem215$SEX,levels=c(1,2),labels=c("HOMBRES","MUJERES"))
### Obtiene la variable SEX(Hombre y mujer) a la cual asigna etiquetas a los niveles
c2<-wtd.table(sdem215$SEX,weights = sdem215$FAC)
c2

View(sdem215$SEX)

#######EJercicio clase, etiquetar la variable NAC_MES

sdem215$NAC_MES<-ordered(sdem215$NAC_MES,levels=c("01","02","03","04","05","06","07","08","09","10","11","12","99"),labels=c("ENERO","FEBRERO","MARZO","ABRIL","MAYO","JUNIO","JULIO","AGOSTO","SEPTIEMBRE","OCTUBRE","NOVIEMBRE","DICIEMBRE","NO ESPECIFICADO"))
### Obtiene la variable SEX(Hombre y mujer) a la cual asigna etiquetas a los niveles
### los numeros van entre comillas porque son caracteres
c3<-wtd.table(sdem215$NAC_MES,weights = sdem215$FAC)
c3
table(c3)
