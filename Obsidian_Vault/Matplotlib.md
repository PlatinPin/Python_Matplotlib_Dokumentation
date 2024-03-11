# Matplotlib
___

![[deckblatt_matplitlib.png]]
## Inhaltsverzeichnis
- [Grundlagen des Plottens](#Grundlagen%20des%20Plottens)
	- [Graphische Darstellung von Funktionen](#Graphische%20Darsellung%20von%20Funktionen)
	- [Linienstil und Linientypen](#Linienstil%20und%20Linientypen)
	- [Linien-Style inderviduell anpssen](#Linien-Style%20inderviduell%20anpassen)
	- [Linienstil und Kontur](#Linienstil%20und%20Kontur)
	- [Transparenz von Linien](#Transparenz%20von%20Linien)
	- [Verwendung von Marker](#Verwendung%20von%20Marker)
	- [Anpassung der Markergröße](#Anpassung%20der%20Markergröße)
	- [Farben](#Farben)
- [Anpassung und Gestaltung](#Anpassung%20und%20Gestaltung)
	- [Raster einfügen](#Raster%20einfügen)
	- [Anpassung der Hintergrundfarbe](#Anpassung%20der%20Hintergrundfarbe)
	- [Auf einen Punkt zeigen](#Auf%20einen%20Punkt%20zeigen)
	- [Einfügen von Pfeilen](#Einfügen%20von%20Pfeilen)
	- [Texteinbindung](#Texteinbindung)
	- [Anpassung des Textstils](#Anpassung%20des%20Textstils)
	- [Rahmung von Text mit einer Box](#Rahmung%20von%20Text%20mit%20einer%20Box)
	- [Title](#Title)
	- [TeX-Markup verwenden](#TeX-Markup%20verwenden)
- [Achsen und Koordinatensysteme](#Achsen%20und%20Koordinatensysteme)
	- [Achsenunsichtbar machen](#Achsenunsichtbar%20machen)
	- [Kartetisches Koordinatensystem](#Kartetisches%20Koordinatensystem)
	- [Verwendung einer logarithmischen Skala](#Verwendung%20einer%20logarithmischen%20Skala)
	- [Achsenbegrenzung](#Achsenbegrenzung)
- [Visualisierung von Daten](#Visualisierun%20von%20Daten)
	- [Legende](#Legende)
	- [Mehrere Plots](#Mehrere%20Plots)
	- [Figures](#Figures)
	- [Flächen einfärben](#Flächen%20einfärben)
	- [Plot im Plot](#Plot%20im%20Plot)
	- [Sub-Plots](#Sub-Plots)
	- [Ploten mit fehlenden Werten](#Ploten%20mit%20fehlenden%20Werten)
- [Fortgeschrittene Visualiserungstechniken](#Fortgeschrittene%20Visualiserungstechniken)
	- [Plots Interaktv gestalten](#Plots%20Interaktiv%20gestalten)
	- [Histogramm](#Histogramm)
	- [Bar-Charts](#Bar-Charts)
	- [Balken Horizontal](#Balken%20Horizontal)
	- [Gruppierte  Bar-Charts](#Gruppierte%20Bar-Charts)
	- [Gestapelte Bar Charts](#Gestapelte%20Bar%20Charts)
	- [Kreis-Diagramm](#Kreis-Diagramm)
	- [Tabellarische Darstellung](#Tabellarische%20Darstellung)
	- [Höhenlinien](#Höhenlinien)
	- [Entfernen von Koordinatenachsen und Rändern](#Entfernen%20von%20Koordinatenachsen%20und%20Rändern)
	- [3D-Plots](#3D-Plots)
	- [Vektoren](#Vektoren)
	- [Geometrie](#Geometrie)
	- [Animationen](#Animationen)

## Grundlagen des Plottens

### Graphische Darsellung von Funktionen
**plt.plot(x,y)** erstellt einen Liniengraphen, indem es die Werte aus x auf die x-Achse und y auf der y-Achse abbildet.
```python
x_1 = np.linspace(0,5,10)
y_1 = x_1**2
plt.plot(x_1,y_1) # Einfaches Plotten von Dateien, in einem einzelnen Diagramm
```
![[Screenshot 2024-02-16 at 14-28-38 JupyterLite.png]]

### Linienstil und Linientypen

| Zeichen | Beschreibung |
| ---- | ---- |
| - | Durchgezogene Linie |
| -- | Gestrichelte Line |
| -. | Strichpunkt-Linie |
| : | Punktierte Linie |
```python
fig_2, axes_2 = plt.subplots(figsize=(8,4), nrows=1,ncols=4)
plt.tight_layout()

axes_2[0].set_title('Durchgezogene Linie')
axes_2[0].plot(x_1,y_1,'-')
axes_2[1].set_title('Gestrichelte Linie')
axes_2[1].plot(x_1,y_1,'--')
axes_2[2].set_title('Strichpunkt-Linie')
axes_2[2].plot(x_1,y_1,'-.')
axes_2[3].set_title('Punktierte Linie')
axes_2[3].plot(x_1,y_1,':')
```
![[Screenshot 2024-02-16 at 14-28-28 JupyterLite.png]]

### Linien-Style inderviduell anpassen

Der Parameter **dashes=[Linienlänge, Lückenlänge, Linienlänge, ...]** ist ein Teil der Funktion "ax.plot", die verwendet wird, um den Linienstil individuell anzupassen, indem er die Länge der Linienabschnitte und Lücken festlegt.

```python
fig = plt.figure(figsize=(5,4))
axes = fig.add_axes([0,0,1,1])
axes.grid(True)
axes.set_title("Linien-Style inderviduell")
axes.plot(x_1,y_1, dashes=[2, 2, 10, 2], lw=3)
```
![[Screenshot 2024-02-16 at 14-28-17 JupyterLite.png]]
### Linienstil und Kontur

Mit **linewidth** oder **lw** innerhalb der Plot-Funktion kann man die Linien-Breite ändern.

```python
fig_2, axes_2 = plt.subplots(figsize=(8,4), nrows=1,ncols=4)
plt.tight_layout()

axes_2[0].set_title('linewidth=6')
axes_2[0].plot(x_1,y_1,linewidth=6)
axes_2[1].set_title('linewidth=12')
axes_2[1].plot(x_1,y_1,linewidth=12)
axes_2[2].set_title('linewidth=18')
axes_2[2].plot(x_1,y_1,linewidth=18)
axes_2[3].set_title("linewidth=24")
axes_2[3].plot(x_1,y_1,linewidth=24)
```
![[Screenshot 2024-02-16 at 14-28-04 JupyterLite.png]]

### Transparenz von Linien

Mit der Funktion **alpha=** innerhalb der Plot-Funktion kann man die Transparenz des Plots anpassen. Der Alpha-Wert ist eine Dezimalzahl zwischen 0 und 1, wobei 0 für vollständig transparent steht und 1 für vollständig undurchsichtig steht.

```python
fig_1, axes_1 = plt.subplots(figsize=(8,4), nrows=1, ncols=4)
plt.tight_layout()
axes_1[0].set_title('25% Alpha')
axes_1[0].plot(x_1,y_1,alpha=0.25, lw=4)
axes_1[1].set_title('50% Alpha')
axes_1[1].plot(x_1,y_1,alpha=0.5, lw=4)
axes_1[2].set_title('75% Alpha')
axes_1[2].plot(x_1,y_1,alpha=0.75, lw=4)
axes_1[3].set_title('100% Alpha')
axes_1[3].plot(x_1,y_1,alpha=1,lw=4)
```
![[Screenshot 2024-02-16 at 14-27-42 JupyterLite.png]]

### Verwendung von Marker
| Nr. | Zeichen | Beschreibung |
| ---- | ---- | ---- |
| 1. | . | Punkt-Marker |
| 2. | , | Pixel-Marker |
| 3. | o | Kreis-Marker |
| 4. | v | Dreiecks-Marker 1 |
| 5. | ^ | Dreiecks-Marker 2 |
| 6. | < | Dreiecks-Marker 3 |
| 7. | > | Dreiecks-Marker 4 |
| 8. | 1 | Tri-Runter-Marker |
| 9. | 2 | Tri-Hoch-Marker |
| 10. | 3 | Tri-Links-Marker |
| 11. | 4 | Tri-Rechts-Marker |
| 12. | s | Quadratischer-Marker |
| 13. | p | Fünfeckiger-Marker |
| 14. | *h* | Sechseck-Marker 1 |
| 15. | H | Sechseck-Marker 2 |
| 16. | + | Plus-Marker |
| 17. | x | x-Marker |
| 18. | D | Rautenförmiger-Marker |
| 19. | d | Dünner Rautenförmiger-Marker |
| 20 | \| | Vertikale Linien-Marker |
| 21. | - | Horizontale Linien-Maker |
| 22. | * | Stern-Marker |
```python
fig_3, axes_3 = plt.subplots(figsize=(25,15),nrows=5, ncols=5)
plt.tight_layout()

axes_3[0][0].set_title('Punkt-Marker')
axes_3[0][0].plot(x_1,y_1,'.')

axes_3[0][1].set_title('Pixel-Marker')
axes_3[0][1].plot(x_1,y_1,',')

axes_3[0][2].set_title('Kreis-Marker')
axes_3[0][2].plot(x_1,y_1,'o')

axes_3[0][3].set_title('Dreiecks-Marker 1')
axes_3[0][3].plot(x_1,y_1,'v')

axes_3[0][4].set_title('Dreiecks-Marker 2')
axes_3[0][4].plot(x_1,y_1,'^')

axes_3[1][0].set_title('Dreiecks-Marker 3')
axes_3[1][0].plot(x_1,y_1,'<')

axes_3[1][1].set_title('Dreiecks-Marker 4')
axes_3[1][1].plot(x_1,y_1,'>')

axes_3[1][2].set_title('tri-runter-Marker')
axes_3[1][2].plot(x_1,y_1,'1')

axes_3[1][3].set_title('tri-hoch-Marker')
axes_3[1][3].plot(x_1,y_1,'2')

axes_3[1][4].set_title('tri-links-Marker')
axes_3[1][4].plot(x_1,y_1,'3')

axes_3[2][0].set_title('tri-rechts-Marker')
axes_3[2][0].plot(x_1,y_1,'4')

axes_3[2][1].set_title('Quadratischer-Marker')
axes_3[2][1].plot(x_1,y_1,'s')

axes_3[2][2].set_title('Fünfeckiger-Marker')
axes_3[2][2].plot(x_1,y_1,'p')

axes_3[2][3].set_title('Stern-Marker')
axes_3[2][3].plot(x_1,y_1,'*')

axes_3[2][4].set_title('Sechseck-Marker 1')
axes_3[2][4].plot(x_1,y_1,'h')

axes_3[3][0].set_title('Sechseck-Marker 2')
axes_3[3][0].plot(x_1,y_1,'H')

axes_3[3][1].set_title('Plus-Marker')
axes_3[3][1].plot(x_1,y_1,'+')

axes_3[3][2].set_title('x-Marker')
axes_3[3][2].plot(x_1,y_1,'x')

axes_3[3][3].set_title('Rautenförmiger-Marker')
axes_3[3][3].plot(x_1,y_1,'D')

axes_3[3][4].set_title('dünner rautenförmiger Marker')
axes_3[3][4].plot(x_1,y_1,'d')

axes_3[4][0].set_title('Vertikale Linie')
axes_3[4][0].plot(x_1,y_1,'|')

axes_3[4][1].set_title('Horizontale Linie')
axes_3[4][1].plot(x_1,y_1,'_')

fig_3.delaxes(axes_3[4][2])
fig_3.delaxes(axes_3[4][3])
fig_3.delaxes(axes_3[4][4])
```
![[Screenshot 2024-02-16 at 14-37-40 JupyterLite.png]]

### Anpassung der Markergröße

Mit **markersize** oder **ms** innerhalb der Plot-Funktion, kann man die Größe der Marker ändern.

```python
fig_2, axes_2 = plt.subplots(figsize=(8,4), nrows=1,ncols=4)
plt.tight_layout()

axes_2[0].set_title('markersize=3')
axes_2[0].plot(x_1,y_1,'x',markersize=3)
axes_2[1].set_title('markersize=6')
axes_2[1].plot(x_1,y_1,'x',markersize=6)
axes_2[2].set_title('markersize=12')
axes_2[2].plot(x_1,y_1,'x',markersize=12)
axes_2[3].set_title("markersize=16")
axes_2[3].plot(x_1,y_1,'x',markersize=16)
```
![[Screenshot 2024-02-16 at 14-38-33 JupyterLite.png]]

### Farben

| Zeichen | Farbe |
| ---- | ---- |
| b | Blau |
| g | Grün |
| r | Rot |
| c | Cyan |
| m | Magenta |
| y | Gelb |
| k | Schwarz |
| w | Weiß |

## Anpassung und Gestaltung

### Raster einfügen
Mit der Funktion **grid(True, color=,dashes=())** wird in dem Diagramm ein Raster eingefügt.

Mit dashes wird das Muster des Rasters eingestellt. (Anzahl Linien, Anzahl Pausen, Anzahl Linien, Anzahl Pausen ....)

```python
fig_1 = plt.figure(figsize=(5,4))
axes_1 = fig_1.add_axes([0,0,1,1])
axes_1.set_title('Raster')
axes_1.grid(True, color='0.6', dashes=(5,2,1,2))
axes_1.plot(x_1,y_1)
```
![[Screenshot 2024-02-16 at 14-40-42 JupyterLite.png]]

### Anpassung der Hintergrundfarbe

Mit der Funktion **facecolor()** kann man beliebig die Hintergrundfarbe des Plots anpassen.

```python
fig_1 = plt.figure(figsize=(5,4))
axes_1 = fig_1.add_axes([0,0,1,1])
axes_1.set_title('Hintergrundfarbe')
axes_1.set_facecolor('#FAEBD7')
axes_1.grid(True)
axes_1.plot(x_1,y_1)
```

![[Screenshot 2024-02-16 at 14-41-14 JupyterLite.png]]

### Auf einen Punkt zeigen

Mit der Funktion **plt.annotate('Text', xy=(x,y),xytext=(x,y),arrowprops=dict(facecolor='black', shrink=0.05))** kann man mit einem Pfeil auf einen bestimmten Punkt verweisen. Mit den optimalen Parametern facecolor kann man die Farbe des Pfeils ändern und mit shrink bestimmen, um wie viel Prozent der Pfeil kleiner sein soll, damit er nicht direkt auf deinen Punkt zeigt.

```python
fig_1 = plt.figure(figsize=(5,4),dpi=100)
axes_1 = fig_1.add_axes([0,0,1,1])
axes_1.set_title('Auf einen Punkt verweisen')
axes_1.annotate('Ein Punkt',xy=(2,4),xytext=(3,3.5),arrowprops=dict(facecolor='black', shrink=0.05))
axes_1.plot(x_1,y_1)
```

![[Screenshot 2024-02-16 at 14-42-06 JupyterLite.png]]
### Einfügen von Pfeilen

Mit **plt.arrow(x=, y=, dx=, dy=)** kann ein Pfeil ins Koordinatensystem geplottet werden. Dabei steht x und y für die Koordinaten, an denen der Pfeil startet und dx und dy für die Länge des Pfeiles.

```python
fig_1 = plt.figure(figsize=(5,4),dpi=100)
axes_1 = fig_1.add_axes([0.1,0.1,0.9,0.9])
axes_1.set_title('Pfeil im Plot')
plt.arrow(x=4, y=6, dx=2, dy=2, width=0.04)
plt.arrow(x=6, y=7.8, dx=-1.5, dy=-1.5, width=0.04)
```

![[Screenshot 2024-02-16 at 14-42-46 JupyterLite.png]]

### Texteinbindung

Mit der Funktion **plt.text(x, y, Text)** kann man in einen Plot einen eigenen Text einfügen. Dabei definiert x und y die Position im Plot und Text, was an der gewählten Stelle stehen soll.

```
x = [3, 6, 8, 12, 14]
y = [4, 9, 14, 12, 9]

plt.title('Text im Plot')
plt.plot(x,y,'bo')
plt.text(6, 9.5, 'A piece of text')
```

![[Screenshot 2024-02-16 at 14-43-21 JupyterLite.png]]

### Anpassung des Textstils

font = {'family': 'serif',  
'color': 'red',  
'weight': 'bold',  
'size': 20  
}  

family -> Gibt die Schriftart an. 
color -> Die Schriftfarbe 
weight -> Schrift Eigenschaft (normal, bold, light) 
size -> Schriftgröße in px

```python
x = [3, 6, 8, 12, 14]
y = [4, 9, 14, 12, 9]

font = {'family': 'serif',
        'color':  'red',
        'weight': 'bold',
        'size': 20
        }

plt.title('Text im Plot')
plt.plot(x,y,'bo')
plt.text(6, 9.5, 'A piece of text', fontdict=font)
```

![[Screenshot 2024-02-16 at 14-43-58 JupyterLite.png]]

### Rahmung von Text mit einer Box

box = {'facecolor': 'none',  
'edgecolor': 'green',  
'boxstyle': 'round'  
}  

facecolor -> Hintergrundfarbe  
edgecolor -> Farbe des Rahmens

| Boxstyle |
| ---- |
| circle |
| darrow |
| larrow |
| rarrow |
| round |
| round4 |
| roundtooth |
| sawtooth |
| square |

```python
box_r = {'facecolor': 'none',
       'edgecolor': 'green',
       'boxstyle': 'round'
      }

box_c = {'facecolor': 'none',
       'edgecolor': 'green',
       'boxstyle': 'circle'
      }

box_d = {'facecolor': 'none',
       'edgecolor': 'green',
       'boxstyle': 'darrow'
      }

box_la = {'facecolor': 'none',
       'edgecolor': 'green',
       'boxstyle': 'larrow'
      }

box_ra = {'facecolor': 'none',
       'edgecolor': 'green',
       'boxstyle': 'rarrow'
      }

box_r4 = {'facecolor': 'none',
       'edgecolor': 'green',
       'boxstyle': 'round4'
      }

box_rt = {'facecolor': 'none',
       'edgecolor': 'green',
       'boxstyle': 'roundtooth'
      }

box_sa = {'facecolor': 'none',
       'edgecolor': 'green',
       'boxstyle': 'sawtooth'
      }

box_s = {'facecolor': 'none',
       'edgecolor': 'green',
       'boxstyle': 'square'
      }

plt.title('Text Boxen')
plt.plot(6, 9.5, 'bo', ms=2)

plt.text(6, 9.5, 'round', bbox=box_r)
plt.text(6, 9.7, 'circle', bbox=box_c)
plt.text(6, 9.9, 'darrow' ,bbox=box_d)
plt.text(6, 9.3, 'larrow', bbox=box_la)
plt.text(6, 9.1, 'rarrow', bbox=box_ra)

plt.text(5.8, 9.5, 'round4', bbox=box_r4)
plt.text(5.8, 9.3, 'roundtooth', bbox=box_rt)
plt.text(5.8, 9.1, 'sawtooth', bbox=box_sa)
plt.text(5.8, 9.7, 'square', bbox=box_s)
```

![[Screenshot 2024-02-16 at 14-45-52 JupyterLite.png]]

### Title

**plt.title('Title')** setzt den Title für den erstellten Diagrammplot fest.

```python
x_1 = np.linspace(0,5,10)
y_1 = x_1**2
plt.title('Days Squared Chart') # Ein Diagramm mit Title versehen.
plt.plot(x_1,y_1)
```

![[Screenshot 2024-02-16 at 14-46-28 JupyterLite.png]]

### TeX-Markup verwenden

Indem man innerhalb eines Rohe-Strings zwei \$$ einfügt, kann man TeX Markup benutzen, innerhalb seiner Plots.

```python
fig_1 = plt.figure(figsize=(5,4))
axes_1 = fig_1.add_axes([0,0,1,1])
axes_1.set_title('TeX Markup')
axes_1.text(0, 23,
            r'$\delta_i \gamma^{ij} \sum_{i=0}^\infty x_1 \frac{3}{4}$')
axes_1.text(0,18,
            r'$\frac{8 - \frac{x}{5}}{8} \sqrt{\pi} \sin(\pi) \sqrt[3]{8}$')

axes_1.plot(x_1,y_1)
```

![[Screenshot 2024-02-16 at 14-47-34 JupyterLite.png]]

## Achsen und Koordinatensysteme

### Achsenunsichtbar machen

Mit **axes.get_xaxis().set_visible(False)** und **axes.get_yaxis().set_visible(False)**, kann jeweils die x-Achse, sowie auch die y-Achse unsichtbar gemacht werden.

```python
x_1 = np.linspace(0,5,10)
y_1 = x_1**2
fig_1 = plt.figure(figsize=(5,4))
axes_1 = fig_1.add_axes([0,0,1,1])
axes_1.set_title('Achsen entfernen')
axes_1.get_xaxis().set_visible(False)
axes_1.get_yaxis().set_visible(False)
axes_1.plot(x_1,y_1)
```

![[Screenshot 2024-02-16 at 14-48-57 JupyterLite.png]]


### Kartetisches Koordinatensystem

Mit **spines[''].set_position('')** kann man die Position der Achsen verschieben. Es gibt 4 Achsen im Koordinatensystem: Top, bottom, right und left.

Mit **spines[''].set_color('')** kann man die Farbe der jeweiligen Achse anpassen und mit 'none' unsichtbar machen.

**ax.plot(0,1, ">k", transform=axes_1.get_yaxis_transform(), clip_on=False)**, erstellt die Pfeile an den Koordinatenachsen enden. Die 0,1 gibt dabei die x bzw. y Koordinate an, dabei ist 0 ganz Links vom Diagramm und 1 ganz Rechts von Diagramm. Die Funktion transform=ax.get_yaxis_transform() macht, dass die y-Koordinate exakt an die y-Achse bezogen ist (für x genau so). Clip_on gibt an, ob der Pfeil abgeschnitten werden soll, falls er außerhalb des Diagramms ist.

```python
from mpl_toolkits.axisartist.axislines import AxesZero

fig_1 = plt.figure(figsize=(5,4))
axes_1 = fig_1.add_axes([0,0,1,1])
axes_1.set_title('Kartetisches Koordinatensystem')

axes_1.spines['bottom'].set_position('zero')
axes_1.spines['left'].set_position('zero')
axes_1.spines['top'].set_color('none')
axes_1.spines['right'].set_color('none')

axes_1.plot(1, 0, ">k", transform=axes_1.get_yaxis_transform(), clip_on=False)
axes_1.plot(0, 1, "^k", transform=axes_1.get_xaxis_transform(), clip_on=False)

axes_1.plot(x_1,y_1)
```

![[Screenshot 2024-02-16 at 14-49-46 JupyterLite.png]]

### Verwendung einer logarithmischen Skala

Mit den Funktionen **xscale('log')** oder **yscale('log')** kann man die jeweiligen Achsen in einem logarithmischen Maßstab skalieren.

```python
fig_1 = plt.figure(figsize=(5,4))
axes_1 = fig_1.add_axes([0,0,1,1])
axes_1.set_title('Log')
axes_1.set_yscale('log')
axes_1.plot(x_1,y_1)
```

![[Screenshot 2024-02-16 at 14-50-28 JupyterLite.png]]

### Achsenbegrenzung

Mit den Funktionen **xlin([x,y])** und **ylim([x,y])** kann man die Achsen beliebig begrenzen.

```python
fig_1 = plt.figure(figsize=(5,4))
axes_1 = fig_1.add_axes([0,0,1,1])
axes_1.set_title('Achsen begrenzen')
axes_1.set_xlim([0,3])
axes_1.set_ylim([0,8])
axes_1.plot(x_1,y_1)
```

![[Screenshot 2024-02-16 at 14-51-02 JupyterLite.png]]

## Visualisierung von Daten

### Legende

Mit **legend(loc=)** kann eine Legende zum Plot hinzugefügt werden.  
**upper right**  
**upper left**  
**lower left**  
**lower right**  
oder eine tulpe aus (x, y) Koordinaten.  

Um die Legende exakt zu positionieren, unter anderem auch außerhalb des Plots, kann folgender Befehl benutzt werden: **plt.legend(loc='right', bbox_to_anchor=(1, 0, 0.5, 1))** dabei steht **bbox_to_anchor=(x, y, width, height)** Alternative kann einfach nur **axes.legend(loc=)** benutzt werden, um eine Legende innerhalb des Plots zu erstellen.

```python
fig_1 = plt.figure(figsize=(5,4))
axes_1 = fig_1.add_axes([0,0,1,1])
axes_1.set_title('Achsen begrenzen')
axes_1.set_xlim([0,3])
axes_1.set_ylim([0,8])
axes_1.plot(x_1,y_1, label='x^2 Werte')
axes_1.legend(loc='right', bbox_to_anchor=(0.8,0,0.5,1.7))
```

![[Screenshot 2024-02-16 at 14-52-00 JupyterLite.png]]

### Mehrere Plots

**plt.subplot(Spalte, Zeilen, Position)** erzeugt eine Rasteranordnung von Plots, wobei die Reihenfolge Spalte, Zeile und dann die ausgewählte Position ist.


```python
plt.subplot(1,2,1) # Erstellt ein Sub-Plot (Spalten,Zeilen,Adresse)
plt.plot(x_1,y_1,'r')
plt.subplot(1,2,2)
plt.plot(x_1,y_1,'b')
```

![[Screenshot 2024-02-16 at 15-52-01 JupyterLite.png]]

### Figures

Der Begriff "Figures" bezieht sich auf die oberste Ebene von Diagrammen, die als Leinwand für Plots dienen, auf denen mehrere Subplots oder Grafikelemente angeordnet werden können. Diese "Figures" sind wichtig, da sie die grundlegende Zeichenfläche für Diagramme bereitstellen, auf der Plots, Achsen, Beschriftungen und andere Elemente angeordnet werden können. Sie ermöglichen die Strukturierung und Organisation von Grafiken, was besonders nützlich ist, wenn mehrere Plots oder Subplots in einer einzigen Ausgabe benötigt werden.

**plt.figure(figsize=(x,y),dip=100)** erstellt eine neue Matplotlib-Figur mit einer Größe von 5X4 und einer Auflösung von 100 DPI (Dots per inch)

**.legend(loc=)** wird verwendet, um eine Legende zu einem Diagramm hinzuzufügen. Dabei gibt es mehrere Möglichkeiten, die Position zu wählen.

| loc=  | Position                 |
| ----- | ------------------------ |
| 0     | System wählt automatisch |
| 1     | Oben Rechts              |
| 2     | Oben Links               |
| 3     | Unten Links                         |
| 4     | Unten Rechts                         |
| (x,y) | Frei im Diagramm wählbar                         |

```python
fig_1 = plt.figure(figsize=(5,4),dpi=100) # Erstellt eine Figure. Figsize gibt die größe des Diagramms an
# dpi gibt den zoom an (100%)
axes_1 = fig_1.add_axes([0.1,0.1,0.9,0.9]) # fügt die Achsen hinzu (left, bottom, width, height)
axes_1.set_xlabel('Days') # X-Achsen beschrieftung
axes_1.set_ylabel('Days Squared') # Y-Achsen beschrieftung
axes_1.set_title('Days Squared Chart') # Title des Diagramms
axes_1.plot(x_1,y_1,label='x/x^2') # Plot mit label
axes_1.plot(y_1,x_1,label='x^2/x')
axes_1.legend(loc=0) # Eine legend mit den jeweiligen labels erstellen. loc=0 wählt die beste position automatisch aus.
# upper right: 1, upper left: 2, lower left: 3, lower right: 4
# or supply a tuple of x & y from lower left
```

![[Screenshot 2024-02-16 at 15-54-26 JupyterLite.png]]


### Flächen einfärben

Mittels Matplotlib ist es auch möglich, Flächen in einem Plot einzufärben und damit visuell hervorzuheben. Dafür wird die Funktion **ax.fill_between(x,y,where=,facecolor=,alpha=,legend=)** verwendet. Dabei kann mit where=, eine Bedingung eingegeben werden für die Einfärbung.

```python
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0,5,100)
y1 = (x-3)**2
y2 = -(x-2)**2+8

fig = plt.figure()
ax = fig.add_axes([0.1,0.1,0.9,0.9])
ax.plot(x,y1,x,y2, color='black')
ax.grid(True)
ax.fill_between(x,y1,y2,where=y2>=y1, facecolor='b',alpha=0.2)
```
![[f_01.png]]

```python
import matplotlib.pyplot as plt
import numpy as np

t = np.linspace(0,40,500)
y = 20 * np.sin(2*np.pi*50*t*np.float_power(10,-3))

fig = plt.figure()
ax = fig.add_axes([0.1,0.1,0.9,0.9])
ax.plot(t,y,color='k')
ax.grid(True)
ax.fill_between(t,y,where=y>=0, facecolor='b', alpha=0.2, label='Positiver Anteil')
ax.fill_between(t,y,where= y<=0, facecolor='g', alpha=0.2, label='Negativer Anteil')
ax.legend(loc=0)
```
![[f_02.png]]

### Plot im Plot

```python
fig_1 = plt.figure(figsize=(5,4),dpi=100)
axes_1 = fig_1.add_axes([0.1,0.1,0.9,0.9])
axes_1.set_xlabel('Days')
axes_1.set_ylabel('Days Squared')
axes_1.set_title('Days Squared Chart')
axes_1.plot(x_1,y_1,label='x/x^2')
axes_1.plot(y_1,x_1,label='x^2/x')
axes_1.legend(loc=1)

# Erstellt einen Plot, innerhalb eines Plots
axes_2 = fig_1.add_axes([0.45, 0.45, 0.4, 0.35])
axes_2.set_xlabel('Days')
axes_2.set_ylabel('Days Squared')
axes_2.set_title('Days Squared Chart')
axes_2.plot(x_1,y_1,'r')

axes_2.text(0,35,'Message') # fügt einen Text hinzu
```

![[Screenshot 2024-02-16 at 15-54-56 JupyterLite.png]]

### Sub-Plots

```python
fig_2, axes_2 = plt.subplots(figsize=(8,4), nrows=1, ncols=3)
plt.tight_layout()
axes_2[1].set_title('Plot 2')
axes_2[1].set_xlabel('x')
axes_2[1].set_ylabel('x Squared')
axes_2[1].plot(x_1,y_1)
```

![[Screenshot 2024-02-16 at 15-55-26 JupyterLite.png]]

### Ploten mit fehlenden Werten

Mit der NumPy-Funktion **np.nan** kann man fehlende Werte in seinen Datensatz hinzufügen; diese werden Lücken, kennzeichnen sich dadurch, dass sie nicht verbunden werden.

```python
import numpy as np
x_2 = np.arange(-1.5, 1.75, 0.25)
y_2 = [0, 1, 1.5, 2, np.nan, 2.3, 2.5, np.nan, 2.3, 2, np.nan, 1.5, 1.0]
fig = plt.figure(figsize=(5,4))
axes2 = fig.add_axes([0,0,1,1])
axes2.grid(True)
axes2.plot(x_2, y_2)
```

![[Screenshot 2024-02-16 at 15-56-09 JupyterLite.png]]

## Fortgeschrittene Visualiserungstechniken

### Plots Interaktiv gestalten

In Matplotlib ist es möglich, direkt Plots interaktiv zu gestalten, allerdings ist diese Funktion eher begrenzt nutzbar und für "aufwändigere"-Programme sollte eher auf Tkinter oder PyQt5 zurückgegriffen werden.

```python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.widgets import Slider, Button

t = np.linspace(0,1,200)
a0 = 5
f0 = 5
s = a0*np.sin(2*np.pi*f0*t)

fig = plt.figure(figsize=(10,6))
ax = fig.add_axes([0.25,0.30,0.9,0.9])
ax.axis([0,1,-10,10])
ax.grid(True)
kurve, = ax.plot(t,s,lw=2,color='k')

#Objekt für die Plazierung der Steuerelemente
#Linker Rand, unterer Rand, länge, höhe
xyAmp = fig.add_axes([0.35,0.15,0.7,0.05])
xyFre = fig.add_axes([0.35,0.1,0.7,0.05])
xyRes = fig.add_axes([0.8,0.025,0.1,0.05])

#Objekte für Steuerelemente erzeugen
#(Koordinaten,Text,Kleinster-Wert,Größter-Wert,Startwert,Step-Größe)
sldAmp = Slider(xyAmp,'Amplitude',1,10,valinit=a0,valstep=0.1)
sldFre = Slider(xyFre,'Frequenz',1,10,valinit=f0,valstep=0.1)
bRes = Button(xyRes, 'Reset')

#Funktion um Variablen und Funktion updaten
def update(val):
    A = sldAmp.val
    F = sldFre.val
    kurve.set_data(t,A*np.sin(2*np.pi*F*t))

#Funktion um den Plot zu Reseten
def reset(event):
    sldAmp.reset()
    sldFre.reset()

#Funktion der Steurelemente implementieren
sldAmp.on_changed(update)
sldFre.on_changed(update)
bRes.on_clicked(reset)
```
![[i01.png]]
### Histogramm

Histogramme zeigen die Verteilung von Daten in verschiedenen Kategorien oder Intervallen gut an. Es besteht aus Balken, die die Häufigkeit oder Anzahl der Datenpunkte in jedem Intervall darstellen, wodurch man schnell Einsicht in die Datenverteilung gewinnt.

Mit der Funktion **plt.hist(Array, bins=, density=, stacked=)** kann man ein Histogramm ploten.

Dabei bedeutet **bins=** die Anzahl, in wie viele Intervalle der Datensatz eingeteilt werden soll.

Wenn **density=** auf True gesetzt ist, gibt die y-Achse die Wahrscheinlichkeitsdichte an, in Bezug auf wie häufig der Datenpunkt aufgetreten ist. Falls density auf False gesetzt ist, repräsentieren die Balken die absolute Häufigkeit der Daten.

Ist **stacked=** True, werden mehrere Datensätze innerhalb eines Histogramms übereinander gelegt; falls auf false, sind die verschiedenen Datensätze nebeneinander.

```python
arr_1 = np.random.randint(1,7,5000)
arr_2 = np.random.randint(1,7,5000)
arr_3 = arr_1 + arr_2

fig_1 = plt.figure(figsize=(5,4))
axes_1 = fig_1.add_axes([0,0,1,1])
axes_1.hist(arr_3, bins=11, density=True, stacked=True)
```

![[Screenshot 2024-02-16 at 15-57-09 JupyterLite.png]]

### Bar-Charts

```python
x = ['Nuclear', 'Hydro', 'Coal', 'Gas' , 'Solar', 'Wind', 'Other']
per_1 = [71, 10, 3, 7, 2, 4, 3]
variance = [8, 3, 1, 3, 1, 2, 1]

fig_1 = plt.figure(figsize=(5,4))
axes_1 = fig_1.add_axes([0,0,1,1])
axes_1.bar(x, per_1, color='purple', yerr=variance)
```

![[Screenshot 2024-02-16 at 15-57-37 JupyterLite.png]]

#### Balken Horizontal

```python
x = ['Nuclear', 'Hydro', 'Coal', 'Gas' , 'Solar', 'Wind', 'Other']
per_1 = [71, 10, 3, 7, 2, 4, 3]
variance = [8, 3, 1, 3, 1, 2, 1]
a
fig_1 = plt.figure(figsize=(5,4))
axes_1 = fig_1.add_axes([0,0,1,1])
axes_1.barh(x, per_1, color='purple')
```

![[Screenshot 2024-02-16 at 15-58-10 JupyterLite.png]]

#### Gruppierte Bar-Charts

**axes_1.bar(x, y, width=, edgecolor='')** erstellt ein Balkendiagramm. width gibt die Breite der jeweiligen Balken an. edgecolor, die Umrandungsfarbe der Balken.

```python
m_eng = (76, 85, 86, 88, 93)
f_eng = (24, 15, 14, 12, 7)

fig_1 = plt.figure(figsize=(5,4))
axes_1 = fig_1.add_axes([0,0,1,1])

spc = np.arange(5)

axes_1.bar(spc, m_eng, width=0.45, label='Male', edgecolor='k')
axes_1.bar(spc + 0.45, f_eng, width=0.45, label='Female', edgecolor='k')
axes_1.set_xticks(spc + 0.45/2, ('Aero', 'Chem', 'Civil', 'Elec', 'Mech'))
```

![[Screenshot 2024-02-16 at 15-58-59 JupyterLite.png]]

#### Gestapelte Bar Charts

Indem **bottom=** benutzt wird, werden an jeder Balkenposition auch die neuen Balken des zweiten Datensatzes eingefügt.

```python
t_type = ['Kind', 'Elem', 'Sec', 'Spec']
m_teach = np.array([2, 20, 44, 14])
f_teach = np.array([98, 80, 56, 86])
ind = [x for x, _ in enumerate(t_type)]

fig_1 = plt.figure(figsize=(5,4))
axes_1 = fig_1.add_axes([0,0,1,1])
axes_1.bar(ind, m_teach, width=0.45, label='Male', bottom=f_teach)
axes_1.bar(ind, f_teach, width=0.45, label='Female')
axes_1.legend(loc='lower right')
```

![[Screenshot 2024-02-16 at 16-00-03 JupyterLite.png]]

### Kreis-Diagramm

Mit **plt.pi(Anzahl,explode=,labels=,colors=,autpct='%1.of%\%startangle=,textprops=dict(color=''"))**  erstellt ein Kreis-Diagramm.  
**Anzahl** gibt die Daten an, die das Diagramm repräsentiert.  
**explode** definiert, welches Stück herausgezogen wird und um wie viel Prozent,  
dazu muss eine Liste übergeben werden, mit so vielen Elementen, wie Tortenstücke im Diagramm.  
**labels** sind die Beschriftungen der Tortenstücke.  
**colors** gibt die Farbe der Tortenstücke an.  
**autopct='%1.0f%\%'** gibt die Prozentwerte ohne Dezimalstellen aus.  
**shadow=True** fügt Schatten zu den Tortenstücken hinzu.  
**startangle=** legt den Winkel fest, unter dem das Torten-Diagramm beginnt.  
**textprops=dict(color='')** legt die Textfarbe für die Tortenstücke fest.

```python
import random

fig_6 = plt.figure(figsize=(5,4))
axes_6 = fig_6.add_axes([0.1,0.1,0.9,0.9])

types = ['Water', 'Normal', 'Flying', 'Grass', 'Psychic', 'Bug', 'Fire', 'Posion',
         'Ground', 'Rock', 'Fighting', 'Dark', 'Steel', 'Electric', 'Dragon', 'Fairy',
         'Ghost', 'Ice']
poke_num = [133, 109, 101, 98, 85, 77, 68, 66, 65, 60, 57, 54, 53, 51, 50, 50, 46, 40]

colors = []
for i in range(18):
    rgb = (random.uniform(0,.5),random.uniform(0,.5),random.uniform(0,.5))
    colors.append(rgb)

explode = [0] * 18 # Liste mit 18 Nullen
explode[0] = 0.2

wedges, texts, autotexts = plt.pie(poke_num, explode=explode, labels=types, colors=colors, 
                                   autopct='%1.0f%%', shadow=True, 
                                   startangle=140, textprops=dict(color='w'))

plt.legend(wedges, types, loc='right', bbox_to_anchor=(1, 0, 0.5, 1))
```

![[Screenshot 2024-02-16 at 16-03-13 JupyterLite.png]]

### Tabellarische Darstellung

Mit Matplotlib ist es auch möglich Tabellen zu erstellen, mit der Funktion **table_1 = ax_1.table(cellText=data, loc='center', cellColours=)** 

**CellText=** Daten die innerhalb der Tabelle stehen sollen.
**loc=** Ausrichtung der Zellen
**CellColours=** Hintergrund der Tabellenfarbe, dabei muss eine Liste übergeben werden, in der jede Zelle Seperat die Farbe angepasst wird [rows * 'g'] * cols.

```python
import matplotlib.pyplot as plt

data = [
    ['Name', 'Alter', 'Stadt', 'Land', 'Beruf'],
    ['Alice', 30, 'New York', 'USA', 'Ingenieur'],
    ['Bob', 25, 'London', 'UK', 'Student'],
    ['', '', '', '', ''],  # Leere Zeile
    ['Charlie', 35, 'Berlin', 'Deutschland', 'Künstler']
]

fig = plt.figure(figsize=(8,8))
gs = fig.add_gridspec(7, 2)

ax_1 = fig.add_subplot(gs[0, 0:1])
ax_1.set_xticks([])
ax_1.set_yticks([])
ax_1.set_frame_on(False)
table_1 = ax_1.table(cellText=data, loc='center', cellColours=[5*'g']*5)
table_1.set_fontsize(20)
table_1.scale(8,3)

```

![[Tabelle_1.png]]

Mit dem zusätzlichen Parameter **colLabels=** kann man eine Liste mit Zeilen Überschrieften übergeben und diese mit **colColours=** einfärben.

```python
data2 = [
    ['Alice', 30, 'New York', 'USA', 'Ingenieur'],
    ['Bob', 25, 'London', 'UK', 'Student'],
    ['', '', '', '', ''],  # Leere Zeile
    ['Charlie', 35, 'Berlin', 'Deutschland', 'Künstler']
]

head = ['Name', 'Alter', 'Stadt', 'Land', 'Beruf']

ax_2 = fig.add_subplot(gs[2, 0:1])
ax_2.set_xticks([])
ax_2.set_yticks([])
ax_2.set_frame_on(False)
table_2 = ax_2.table(cellText=data2, colLabels=head, cellColours=[5*'g']*4, colColours=['r']*5) # [col * 'g'] * row
table_2.set_fontsize(20)
table_2.scale(8,3)
```
![[Tabelle_2.png]]

Dies geht auch mit **rowLabels=** einer zusätzlichen Spalte für Überschrieften erstellen und mit **rowColours=** die Farbe anpassen.

```python
data3 = [
    ['Alice', 30, 'New York', 'USA', 'Ingenieur'],
    ['Bob', 25, 'London', 'UK', 'Student'],
    ['', '', '', '', ''],  # Leere Zeile
    ['Charlie', 35, 'Berlin', 'Deutschland', 'Künstler']
]

rowhead = ['Person 1.', 'Person 2.', 'Person 3.', 'Person 4.']

colhead = ['Name', 'Alter', 'Stadt', 'Land', 'Beruf']

ax_3 = fig.add_subplot(gs[6, 0:1])
ax_3.set_xticks([])
ax_3.set_yticks([])
ax_3.set_frame_on(False)
table_3 = ax_3.table(cellText=data3, cellColours=[5*'g']*4, rowLabels=rowhead, rowColours=['b']*4, colLabels=colhead, colColours=['r']*5)
table_3.set_fontsize(20)
table_3.scale(8,3)
```

![[Tabelle_3.png]]
### Höhenlinien

Um in Python Höhenlinien oder magnetische Felder darstellen zu können, muss ein Netz aus relevanten Punkten über eine Ebene erzeugt werden. Dies kann durch die Numpy-Funktion **np.meshgrid(x,y)** erzeugt werden.

```python
import numpy as np
import matplotlib.pyplot as plt

x=y=np.linspace(1,6,6)
x,y=np.meshgrid(x,y) # Erzeugt ein Netz in der Ebene

fig, ax = plt.subplots(figsize=(10,8))
ax.plot(x,y,marker='x',color='r',ls='none', ms=9)
```
![[1.png]]
Um eine Kontur bzw. Höhenliniendiagramm zu erstellen, wird die Funktion **ax.contour(x,y,H,levels=,colors=)**.   Dabei sind x und y die Koordinaten des Netzes, das durch np.meshgrid erzeugt wurde.   H sind die Werte für jeden Punkt in der Ebene.   levels gibt an, welche Höhenlinien angezeigt werden sollen.

Zusätzlich wird die Funktion **ax.clabel(cp)** verwendet, um die Höhenlinien anzupassen.  
cp ist dabei der Graph und inline gibt an.

Durch die Funktion **ax.set_aspect('equal')** kommt es nicht durch den Bildschirm zu Verzerrungen.

```python
import numpy as np
import matplotlib.pyplot as plt

I = 62.8
rmax = 10
n=100
lvl=[1,2,4,8,16]

x=y=np.linspace(-rmax,+rmax,n)
x,y=np.meshgrid(x,y)

H = I/(2*np.pi*np.hypot(x,y))

fig,ax = plt.subplots(figsize=(10,8))
cp = ax.contour(x,y,H,levels=lvl,colors='red')
ax.clabel(cp)
ax.set_aspect('equal')
```

Mit ax.set_aspect('equal'):
![[2.png]]

Ohne ax.set_aspect('equal'):
![[3.png]]



### Entfernen von Koordinatenachsen und Rändern

Um Felder oder Formen nicht in einem Koordinatensystem zu veranschaulichen, wie zum Beispiel Feldlinien, können die Ränder und Achsen leicht wie folgt entfernt werden. 
**ax.set_xticks([])**  
**ax.set_yticks([])**  
**ax.set_frame_on(False)**

```python
import numpy as np
import matplotlib.pyplot as plt

x=y=np.linspace(1,6,6)
x,y=np.meshgrid(x,y) # Erzeugt ein Netz in der Ebene

fig, ax = plt.subplots(figsize=(10,8))
ax.plot(x,y,marker='x',color='r',ls='none', ms=9)
ax.set_xticks([])
ax.set_yticks([])
ax.set_frame_on(False)
```
![[4.png]]


### 3D-Plots

#### 3D-Linien

Die Funktion **plt.figure(figsize=).add_subplot(projection='3d')** ermöglicht die Visualisierung von dreidimensionalen Objekten, die neben den Achsen x und y auch eine z-Komponente aufweisen. Diese Objekte sind typischerweise keine Körper, sondern können beispielsweise Kurven oder punktuelle Datenrepräsentationen darstellen.

```python
import numpy as np
import matplotlib.pyplot as plt

A = 6
h = 5
omega = 3

t = np.linspace(0,2*np.pi,500)
x = A * np.cos(omega * t)
y = A * np.sin(omega * t)
z = h * t

ax = plt.figure(figsize=(6,6)).add_subplot(projection='3d')
ax.plot(x,y,z,lw=2)
```
![[kurve_3d.png]]

#### 3D-Körper

Für das Erstellen von 3D-Körpern wird die Methode **ax.plot_surface(x, y, z, rstride=, cstride=, color=, edgecolors=)** verwendet. Hierbei legt der Parameter rstride die Schrittweite der horizontalen Linien und cstride die Schrittweite der vertikalen Linien fest. Die Option color definiert die Farbe der Flächenabschnitte, während edgecolors die Farben der horizontalen und vertikalen Linien festlegt.

Zur Erzeugung des Gitters für die Koordinaten ist die Numpy-Funktion np.meshgrid() erforderlich.

```python
import numpy as np
import matplotlib.pyplot as plt

n = 100
R = 2
r = 1

p = np.linspace(0,2*np.pi,n)
t = np.linspace(0,2*np.pi,n)
p,t = np.meshgrid(p, t)

x = (R + r * np.cos(p)) * np.cos(t)
y = (R + r * np.cos(p)) * np.sin(t)
z = r * np.sin(p)

ax = plt.figure(figsize=(6,6)).add_subplot(projection='3d')
ax.plot_surface(x,y,z,rstride=5,cstride=5,color='y',edgecolors='r')
ax.set_zlim(-3,3)
```
![[3d_koeper.png]]

### Vektoren

#### 2D-Darstellung

Die Visualisierung eines 2D-Vektors wird mit der Methode ax.quiver(Fx, Fy, angles="xy", scale_units="xy", scale=1, color=) erreicht. Hierbei gibt angles="xy" den Ausgangspunkt des Vektors an. scale_units="xy" verwendet die Einheit der Achsen für die Skalierung. Der Parameter scale=1 definiert den Skalierungsfaktor des Vektors. Die Farbe des Vektors kann mit dem Parameter color= festgelegt werden.

```python
import matplotlib.pyplot as plt
import numpy as np

F1 = np.array((-6,4))
F2 = np.array((4,-8))
F3 = np.array((4,2))

Fres = F1 + F2 + F3
  
fig, ax = plt.subplots()
ax.axis([-8,8,-9,8])
ax.quiver(F1[0], F1[1], angles="xy", scale_units="xy", scale=1, color='m')
ax.quiver(F2[0], F2[1], angles="xy", scale_units='xy', scale=1, color='g')
ax.quiver(F3[0], F3[1], angles="xy", scale_units='xy', scale=1, color='b')
ax.quiver(Fres[1], Fres[1], angles="xy", scale_units='xy', scale=1, color='r', label="Fres")
ax.legend(loc=0)
```
![[Vektoren_2d.png]]

#### 3D-Darstellung

Für die Visualisierung von Vektoren im 3D-Raum kann dieselbe Funktion wie im 2D-Raum verwendet werden, jedoch ohne die Parameter angles="xy", scale_units="xy" und scale=1.

**ax.quiver(0, 0, 0, Fx[0], Fy[1], Fz[2], color='r', lw=3)**

```python
import numpy as np
import matplotlib.pyplot as plt

F1 = np.array((3, 4, 2))
F2 = np.array((5, 2, -4))
Fres = F1 + F2

ax = plt.figure(figsize=(6,6)).add_subplot(projection='3d')
ax.set_xlim(-8,8)
ax.set_ylim(-8,8)
ax.set_zlim(-8,8)
ax.quiver(0, 0, 0, F1[0], F1[1], F1[2], color='r', lw=3)
ax.quiver(0, 0, 0, F2[0], F2[1], F2[2], color='g', lw=3)
ax.quiver(0, 0, 0, Fres[0], Fres[1], Fres[2], color='b', lw=3, label='Fres')
ax.legend(loc=0)
```
![[3D_Vektor.png]]



#### Vektorfelder

Wenn man np.meshgrid() für x und y verwendet, wird ein Gitternetz erzeugt, das die Basis für die Darstellung eines Vektorfelds bildet.

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.linspace(0, 12, 10)
y = np.linspace(0, 12, 10)

u = 2 # Länge
v = 0 # Richtung

x,y = np.meshgrid(x,y)

fig, ax = plt.subplots()
ax.quiver(x,y,u,v,units='xy',scale=2, color='b')
```
![[Vektorfeld.png]]



### Geometrie

#### Rechteck

Um ein Rechteck mit Matplotlib zu erstellen, verwendet man die Funktion **mlt.patches.Rectangle((x1, y1), b, h, fill=, lw=, edgecolor=, angle=)**. 
Die Parameter (x1, y1) geben die Koordinaten der linken unteren Ecke an, 
b ist die Breite, h ist die Höhe. 
Mit fill kann festgelegt werden, ob das Rechteck farbig ausgefüllt sein soll, 
lw skaliert die Linienstärke, 
edgecolor bestimmt die Randfarbe, 
und angle ermöglicht es, das Rechteck um einen bestimmten Winkel zu drehen.

Um das Rechteck zur Zeichenebene hinzuzufügen, wird **ax.add_patch(rechteck)** verwendet

```python
import matplotlib as mlt
import matplotlib.pyplot as plt

fig, ax = plt.subplots()
ax.axis([-8,8,-8,8])
ax.set_xticks([])
ax.set_yticks([])
ax.set_frame_on(False)

r = mlt.patches.Rectangle((3,3),4,2,fill=False,lw=3,edgecolor='r')
r2 = mlt.patches.Rectangle((-3,-3),4,2,fill=True,color='b',lw=3,edgecolor='b')

ax.add_patch(r)
ax.add_patch(r2)
```
![[rechtecke.png]]




#### Kreis

Die Funktion **plt.patches.Circle((x, y), Radius, fill=, lw=, edgecolor=)** dient dazu, einen Kreis zu erstellen und zu zeichnen. Anschließend kann dieser Kreis mithilfe der Funktion **ax.add_patch(circle)** in den Plot eingefügt werden.

(x,y) -> Die Koordinaten des Mittelpunktes des Kreises.
Radius -> Der Radius des Kreises.
fill -> Einstellung ob der Kreis Farbig ausgefüllt sein soll
lw -> Linienbreite
edgecolor -> Einstellung der Linien Farbe

```python
import matplotlib as mlt
import matplotlib.pyplot as plt

r1 = 10
r2 = 5

fig, ax = plt.subplots()
kreis1 = mlt.patches.Circle((0,0), r1, fill=False, lw=3, edgecolor='b')
kreis2 = mlt.patches.Circle((0,0), r2, fill=True, lw=3, edgecolor='r')
ax.add_patch(kreis1)
ax.add_patch(kreis2)
ax.set_xticks([])
ax.set_yticks([])
ax.set_frame_on(False)
ax.axis([-15,15,-15,15])
ax.set_aspect('equal')
```
![[Kreis.png]]


### Animationen

#### Animation: Sinus

Um Animationen in Matplotlib zu erstellen, benötigt man die Methode **FuncAnimation**, die mittels
**from matplotlib.animation import FuncAnimation**
importiert wird.

Zuerst definiert man die zu animierende Funktion und die Variable, in die Richtung, in der sich die Animation bewegen soll, mittels eines weiteren Parameters k, der die Animation steuert.
```pytho
def f(x, frames):
    return np.sin(x - frames / 20)
```

Anschließend wird die Funktion definiert, die die Animation updatet.
```python
def ani_update(frame):
   line.set_ydata(sinus(x,frame))
   return line,
```

Dabei updatet die Funktion line.set_ydata() die y-Werte nach jedem Frame. Die Funktion muss einen Tupel zurückgeben, daher muss line, benutzt werden.

Zum Schluss wird die FuncAnimation benutzt, mit **ani = FuncAnimation(fig, ani_update, interval=20)**, dabei ist repräsentiert fig den Plot, ani_pdate die Funktion für die Animation und Intervall gibt die Pause zwischen den zu generierenden Bildern in Millisekunden an.

```python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation

def sinus(x,frame):
    return np.sin(x-frame/20) # -frame, damit sich der Winkel der Sin-funktion                                   mit jeden Frame verschiebt
def ani_update(frame):
    line.set_ydata(sinus(x,frame))
    return line,

fig, ax = plt.subplots()
x = np.linspace(0,2*np.pi,200)
line, = ax.plot(x, sinus(x,0), 'r-', lw=3)
ani = FuncAnimation(fig, ani_update, interval=20)
ani.save('ani.gif', writer='pillow', fps=50, dpi=100)
```
![[ani.gif]]

#### Animation: Punkt

Um einen Punkt zu animieren, wird die Variable "Lauf" als Frames definiert, wobei für jeden Datenpunkt ein eigener Frame erstellt und berechnet wird. Dies erfolgt durch das Hinzufügen des Parameters "frames=" in die FuncAnimation-Funktion.

```python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation

# Funktion Definieren für die Animation
def sinus(x):
    y = np.sin(x)
    pl.set_data(x, y)
    return pl,

# Laufvariable bzw. Anzahl der Frames
x = np.linspace(0,4*np.pi,100)

fig = plt.figure()
ax = fig.add_subplot()
pl, = ax.plot([], [], 'ro', ms=5)
ax.axis([0,4*np.pi,-1.5,1.5])
ax.grid(True)
ani = FuncAnimation(fig, sinus, frames=x, interval=20)
```
![[punkt_animieren.gif]]

#### Animation: Funktion schritt für schritt

Um eine Funktion schrittweise zu animieren, geht man ähnlich vor wie im vorherigen Kapitel zur Animation eines Punktes. Allerdings muss hier innerhalb der Funktion eine zweite Laufvariable erstellt werden, damit nicht nur der Punkt zum Zeitpunkt "t" berechnet wird, sondern auch alle Punkte, die vor diesem Zeitpunkt liegen.

```python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation

def sinus(x):
    x2 = np.linspace(0, x, int(25*x))
    y = np.sin(x2)
    pl.set_data(x2, y)
    return pl,

x = np.linspace(0,4*np.pi,100)
fig = plt.figure()
ax = fig.add_subplot()
pl, = ax.plot([], [], 'r', lw=3)
ax.grid(True)
ax.axis([0,4*np.pi,-1.5,1.5])
ani = FuncAnimation(fig, sinus, frames=x, interval=20)
plt.show()
```
![[funktion_animieren.gif]]




