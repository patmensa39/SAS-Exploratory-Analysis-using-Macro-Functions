# SAS-Exploratory-Analysis-using-Macro-Functions
Used Macros, Proc freq and proc Univariate to create basics statistics. 
%let categorical= House_Style Overall_Qual Overall_Cond Year_Built Fireplaces Mo_Sold Yr_Sold Garage_Type_2 Foundation_2
				   Heating_QC Masonry_Veneer Lot_Shape_2 Central_Air;
%let interval= SalePrice Log_Price Gr_Liv_Area Basement_Area Garage_Area Deck_Porch_Area Lot_Area Age_Sold Bedroom_AbvGr Full_Bathroom
			    Half_Bathroom Total_Bathroom;


/*Proc Freq used on the catergorical variables*/

ods graphics;



proc freq data=STAT1.AMESHOUSING3;

tables &categorical / plots=freqplot;

format House_Style $House_Style.

Overall_Qual Overall.

Overall_Cond Overall.

Heating_QC $Heating_QC.

Central_Air $NoYes.

Masonry_Veneer $NoYes.

;

title "Categorical variables frequency Analysis";

run;





/*Proc univariate used on the catergorical variables*/

ods select histogram;

proc univariate data=stat1.ameshousing3 noprint;

var &interval;

histogram &interval / normal kernel;

inset mean std / position=ne;

title "Interval Variable Distribution Analysis";

run;



title; 



















