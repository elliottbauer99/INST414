# INST414

import pandas as pd

pga_stats = pd.read_csv('new_pga.csv')
pga_stats

# Putting table. Sorts putting values from high
putting = pga_stats[['NAME', 'EARNINGS', 'PUTTS']].copy()
x = putting.drop(putting[putting['PUTTS'] == 0.000].index)
x

y = x.sort_values('PUTTS', ascending=False)
y

putting_tail = y.tail(20)
putting_tail
putting_head = y.head(20)
putting_head

print(putting_head['PUTTS'].sum())
print(putting_head['PUTTS'].mean())

print(putting_tail['PUTTS'].sum())
print(putting_tail['PUTTS'].mean())

putting_tail['EARNINGS'].sum()
putting_head['EARNINGS'].sum()
putting_tail['EARNINGS'].sum() - putting_head['EARNINGS'].sum()

pga_stats['Earnings per event'] = pga_stats['EARNINGS'] / pga_stats['EVNTS']
pga_stats['Earnings per event'] = pga_stats['Earnings per event'].round(2)
pga_stats.head(20)

pga_stats.sort_values(by='Earnings per event', ascending=False, inplace=True)
pga_stats.head(20)
