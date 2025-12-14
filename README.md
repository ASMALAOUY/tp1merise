## MCD :

![image alt](https://raw.githubusercontent.com/ASMALAOUY/tp1merise/92dde6cd3df0671089cacb912e543525c605f966/mpd.jpg)

## MPD :

![image alt](https://raw.githubusercontent.com/ASMALAOUY/tp1merise/92dde6cd3df0671089cacb912e543525c605f966/mcd.jpg)

##SGBD


```sql
/*==============================================================*/
/* Nom de SGBD :  MySQL 4.0                                     */
/* Date de création :  14-12-25 20:37:54                        */
/*==============================================================*/


drop index FOURNIR2_FK on FOURNIR;

drop index FOURNIR_FK on FOURNIR;

drop table if exists FOURNIR;

drop table if exists FOURNISSEUR;

drop table if exists PRODUIT;

/*==============================================================*/
/* Table : FOURNIR                                              */
/*==============================================================*/
create table FOURNIR
(
   NUMF                           int                            not null,
   CODEPROD                       int                            not null,
   _PRIXACHAT                     decimal,
   primary key (NUMF, CODEPROD)
)
type = InnoDB;

/*==============================================================*/
/* Index : FOURNIR_FK                                           */
/*==============================================================*/
create index FOURNIR_FK on FOURNIR
(
   NUMF
);

/*==============================================================*/
/* Index : FOURNIR2_FK                                          */
/*==============================================================*/
create index FOURNIR2_FK on FOURNIR
(
   CODEPROD
);

/*==============================================================*/
/* Table : FOURNISSEUR                                          */
/*==============================================================*/
create table FOURNISSEUR
(
   NUMF                           int                            not null,
   NOMF                           longtext,
   ADRESSEF                       longtext,
   primary key (NUMF)
)
type = InnoDB;

/*==============================================================*/
/* Table : PRODUIT                                              */
/*==============================================================*/
create table PRODUIT
(
   CODEPROD                       int                            not null,
   DESIGPROD                      longtext,
   _PRIXUNIT                      decimal(8),
   primary key (CODEPROD)
)
type = InnoDB;

alter table FOURNIR add constraint FK_FOURNIR foreign key (NUMF)
      references FOURNISSEUR (NUMF) on delete restrict on update restrict;

alter table FOURNIR add constraint FK_FOURNIR2 foreign key (CODEPROD)
      references PRODUIT (CODEPROD) on delete restrict on update restrict;

```
