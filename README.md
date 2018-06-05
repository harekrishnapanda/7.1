# 7.1
import numpy as np
import pandas as pd
df = pd.DataFrame({'From_To': ['LoNDon_paris', 'MAdrid_miLAN', 'londON_StockhOlm',
'Budapest_PaRis', 'Brussels_londOn'],
'FlightNumber': [10045, np.nan, 10065, np.nan, 10085],
'RecentDelays': [[23, 47], [], [24, 43, 87], [13], [67, 32]],
'Airline': ['KLM(!)', '<Air France> (12)', '(British Airways. )',
'12. Air France', '"Swiss Air"']})
# 7.1.1
df["FlightNumber"].fillna(df["FlightNumber"].ffill()+10, inplace=True)
df.FlightNumber = df.FlightNumber.astype(int)
# 7.1.2
df['From'] = (df['From_To'].str.split('_').str[0]).str.title()
#7.1.3
df['To'] = (df['From_To'].str.split('_').str[1]).str.title()
# 7.1.4
df=df.drop(['From_To'],axis=1)
#7.1.5
tmplst1 = df['RecentDelays']
x=max(len(tmplst2) for tmplst2 in tmplst1)
lst0=[]
k=0
for i in tmplst1:
    for j in range(x-len(i)):
        i.append('Nan')
listx=df.RecentDelays.tolist()
df_small= pd.DataFrame(listx)
lstnew=[]
for n in range(x):
    lstnew.append('Delay'+str(n+1))
df_small.columns = lstnew
df_final = pd.concat([df,df_small], axis=1)
df=df_final.drop(['RecentDelays'],axis=1)
df
