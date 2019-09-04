---
title: 'Tutorial: Erstellen eines Clusteringmodells in python'
description: Im dritten Teil dieser vierteiligen tutorialreihe erstellen Sie ein K-Means-Modell, um mit SQL Server Machine Learning Services Clustering in python auszuführen.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/27/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e768f213edf27528e38b2f18d719869fbf089f21
ms.sourcegitcommit: ecb19d0be87c38a283014dbc330adc2f1819a697
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2019
ms.locfileid: "70238702"
---
# <a name="tutorial-build-a-clustering-model-in-python-with-sql-server-machine-learning-services"></a>Tutorial: Erstellen eines Clusteringmodells in Python mit SQL Server Machine Learning Services

Im dritten Teil dieser vierteiligen tutorialreihe erstellen Sie ein K-Means-Modell in Python, um Clustering auszuführen. Im nächsten Teil dieser Serie stellen Sie dieses Modell in einer SQL-Datenbank mit SQL Server Machine Learning Services bereit.

In diesem Artikel lernen Sie Folgendes:

> [!div class="checklist"]
> * Definieren der Anzahl von Clustern für einen K-Means-Algorithmus
> * Clustering ausführen
> * Analysieren der Ergebnisse

In [Teil 1](tutorial-python-clustering-model.md)haben Sie die erforderlichen Komponenten installiert und die Beispieldatenbank importiert.

In [Teil 2](tutorial-python-clustering-model-prepare-data.md)haben Sie gelernt, wie Sie die Daten aus einer SQL-Datenbank für die Durchführung von Clustering vorbereiten.

In [Teil 4](tutorial-python-clustering-model-deploy.md)erfahren Sie, wie Sie eine gespeicherte Prozedur in einer SQL-Datenbank erstellen, die basierend auf neuen Daten Clustering in python durchführen kann.

## <a name="prerequisites"></a>Erforderliche Komponenten

* Im dritten Teil dieses Tutorials wird davon ausgegangen, dass Sie die Voraussetzungen von [**Teil 1**](tutorial-python-clustering-model.md)erfüllt und die Schritte in [**Teil 2**](tutorial-python-clustering-model-prepare-data.md)ausgeführt haben.

## <a name="define-the-number-of-clusters"></a>Definieren der Anzahl von Clustern

Zum Clustern der Kundendaten verwenden Sie den **K-Means** -Clustering-Algorithmus, eine der einfachsten und bekanntesten Methoden zum Gruppieren von Daten.
Weitere Informationen zu k-means finden Sie in [einer umfassenden Anleitung zum k-Means-Clustering-Algorithmus](https://www.kdnuggets.com/2019/05/guide-k-means-clustering-algorithm.html).

Der Algorithmus akzeptiert zwei Eingaben: Die Daten selbst und eine vordefinierte Zahl "*k*", die die Anzahl der zu generierenden Cluster darstellt.
Bei der Ausgabe handelt es sich um *k* Cluster mit den Eingabedaten, die zwischen den Clustern partitioniert sind.

Das Ziel von k-means besteht darin, die Elemente in k-Clustern zu gruppieren, sodass alle Elemente im gleichen Cluster einander ähnlich sind als Elemente in anderen Clustern.

Um die Anzahl der Cluster zu ermitteln, die für den Algorithmus verwendet werden sollen, verwenden Sie einen Plot der in Gruppen Summe von Quadraten, und zwar nach Anzahl der extrahierten Cluster. Die geeignete Anzahl von zu verwendenden Clustern ist die Kurve oder der "Bogen" des plotdiagramms.

```python
################################################################################################
## Determine number of clusters using the Elbow method
################################################################################################

cdata = customer_data
K = range(1, 20)
KM = (sk_cluster.KMeans(n_clusters=k).fit(cdata) for k in K)
centroids = (k.cluster_centers_ for k in KM)

D_k = (sci_distance.cdist(cdata, cent, 'euclidean') for cent in centroids)
dist = (np.min(D, axis=1) for D in D_k)
avgWithinSS = [sum(d) / cdata.shape[0] for d in dist]
plt.plot(K, avgWithinSS, 'b*-')
plt.grid(True)
plt.xlabel('Number of clusters')
plt.ylabel('Average within-cluster sum of squares')
plt.title('Elbow for KMeans clustering')
plt.show()
```

![Bogen Diagramm](./media/python-tutorial-elbow-graph.png)

Auf Grundlage des Diagramms sollte *k = 4* ein guter Wert sein. Mit diesem *k* -Wert werden die Kunden vier Cluster gruppieren.

## <a name="perform-clustering"></a>Clustering ausführen

Im folgenden Python-Skript verwenden Sie die kmeans-Funktion aus dem sklearn-Paket.

```python
################################################################################################
## Perform clustering using Kmeans
################################################################################################

# It looks like k=4 is a good number to use based on the elbow graph.
n_clusters = 4

means_cluster = sk_cluster.KMeans(n_clusters=n_clusters, random_state=111)
columns = ["orderRatio", "itemsRatio", "monetaryRatio", "frequency"]
est = means_cluster.fit(customer_data[columns])
clusters = est.labels_
customer_data['cluster'] = clusters

# Print some data about the clusters:

# For each cluster, count the members.
for c in range(n_clusters):
    cluster_members=customer_data[customer_data['cluster'] == c][:]
    print('Cluster{}(n={}):'.format(c, len(cluster_members)))
    print('-'* 17)
print(customer_data.groupby(['cluster']).mean())
```

## <a name="analyze-the-results"></a>Analysieren der Ergebnisse

Nachdem Sie das Clustering mithilfe von K-Means durchgeführt haben, besteht der nächste Schritt darin, das Ergebnis zu analysieren und festzustellen, ob Sie Handlungs relevante Informationen finden können.

Sehen Sie sich die vom vorherigen Skript gedruckten Mittelwerte und Cluster Größen für Clustering an.

```results
Cluster0(n=31675):
-------------------
Cluster1(n=4989):
-------------------
Cluster2(n=1):
-------------------
Cluster3(n=671):
-------------------

         customer  orderRatio  itemsRatio  monetaryRatio  frequency
cluster
0        50854.809882    0.000000    0.000000       0.000000   0.000000
1        51332.535779    0.721604    0.453365       0.307721   1.097815
2        57044.000000    1.000000    2.000000     108.719154   1.000000
3        48516.023845    0.136277    0.078346       0.044497   4.271237
```

Die vier Cluster Mittel werden mithilfe der in [Teil 1](tutorial-python-clustering-model-prepare-data.md#separate-customers)definierten Variablen angegeben:

* *orderratio* = Verhältnis der Rückgabe Reihenfolge (Gesamtzahl der Bestellungen, die teilweise oder vollständig zurückgegeben wurden, und die Gesamtzahl der
* *itemsratio* = Verhältnis von Rückgabe Elementen (Gesamtzahl der zurückgegebenen Elemente im Vergleich zur Anzahl erworbener Elemente)
* *monetaryratio* = Verhältnis der Rückgabe Menge (Gesamtbetrag der zurückgegebenen Elemente im Vergleich zum erworbenen Betrag)
* *Frequency* = Rückgabe Häufigkeit

Data Mining mit K-Means erfordert häufig eine weitere Analyse der Ergebnisse sowie weitere Schritte, um die einzelnen Cluster besser zu verstehen, aber es kann einige gute Leads bereitstellen.
Im folgenden finden Sie eine Reihe von Möglichkeiten, wie Sie diese Ergebnisse interpretieren können:

* Cluster 0 scheint eine Gruppe von Kunden zu sein, die nicht aktiv sind (alle Werte sind null).
* Cluster 3 scheint eine Gruppe zu sein, die in Bezug auf das Rückgabe Verhalten auftritt.

Cluster 0 ist eine Gruppe von Kunden, die offensichtlich nicht aktiv sind. Vielleicht können Sie auf Marketingmaßnahmen für diese Gruppe abzielen, um ein Interesse für Käufe zu initiieren. Im nächsten Schritt Fragen Sie die-Datenbank nach den e-Mail-Adressen von Kunden in Cluster 0 ab, sodass Sie eine Marketing-e-Mail an Sie senden können.

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Wenn Sie dieses Tutorial nicht fortsetzen möchten, löschen Sie die tpcxbb_1gb-Datenbank aus SQL Server.

## <a name="next-steps"></a>Nächste Schritte

Im dritten Teil dieser tutorialreihe haben Sie die folgenden Schritte ausgeführt:

* Definieren der Anzahl von Clustern für einen K-Means-Algorithmus
* Clustering ausführen
* Analysieren der Ergebnisse

Um das Machine Learning-Modell bereitzustellen, das Sie erstellt haben, befolgen Sie den Teil vier dieser tutorialreihe:

> [!div class="nextstepaction"]
> [Tutorial: Bereitstellen eines Clusteringmodells in Python mit SQL Server Machine Learning Services](tutorial-python-clustering-model-deploy.md)