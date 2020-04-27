---
title: Konfigurieren von in-Memory-oder directquery-Zugriff für eine tabellarische Modelldatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a5d439a9-5be1-4145-90e8-90777d80e98b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 55a1a296e6a7b2a2155dea590be9321b22e73451
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66067184"
---
# <a name="configure-in-memory-or-directquery-access-for-a-tabular-model-database"></a>Konfigurieren von speicherinternem oder DirectQuery-Zugriff für eine tabellarische Modelldatenbank
  In diesem Thema wird beschrieben, wie die Verbindungseigenschaften eines bereits bereitgestellten tabellarischen Modells geändert werden, um die Verwendung des Modells im DirectQuery-Modus zu aktivieren.  
  
 Weitere Informationen zu diesen Eigenschaften und zur Konfiguration für die gängigsten Szenarien finden Sie unter [directquery-Bereitstellungs Szenarien &#40;tabellarischen SSAS-&#41;](../directquery-deployment-scenarios-ssas-tabular.md).  
  
## <a name="requirements"></a>Anforderungen  
 Es sind mehrere Schritte nötig, um den DirectQuery-Modus auf ein tabellarisches Modell anwenden zu können. Die Voraussetzungen lauten wie folgt:  
  
1.  Stellen Sie sicher, dass das Modell keine Funktionen hat, die möglicherweise Überprüfungsfehler im DirectQuery-Modus verursachen.  
  
2.  Ändern Sie den Speichermodus für das Modell, um DirectQuery zu unterstützen.  
  
3.  Stellen Sie das Modell in einem Modus bereit, in dem Abfragen in entweder einem hybriden oder reinen DirectQuery-Modus unterstützt werden.  
  
4.  Bearbeiten Sie die Verbindungszeichenfolge in der bereitgestellten Datenbank, um den DirectQuery-Modus zu unterstützen.  
  
 In diesem Thema wird davon ausgegangen, dass Sie das Modell erstellt und überprüft haben und den DirectQuery-Zugriff nur noch von einem Client (beispielsweise [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]) aktivieren müssen.  
  
## <a name="procedure"></a>Verfahren  
  
#### <a name="change-the-connection-string-properties-of-the-model"></a>Ändern der Verbindungszeichenfolgen-Eigenschaften eines Modells  
  
1.  Öffnen Sie in SQL Server Management Studio die Instanz, für die Sie das Modell bereitgestellt haben.  
  
2.  Klicken Sie in Objekt-Explorer mit der rechten Maustaste auf den Namen der Model-Datenbank, und wählen Sie **Eigenschaften**aus.  
  
3.  Suchen Sie die Eigenschaft **directquerymode**. Diese Eigenschaft muss auf einen dieser Werte festgelegt werden, um die Verwendung der relationalen Datenquelle zu aktivieren:  
  
    -   **DirectQuery**  
  
    -   **InMemoryWithDirectQuery**  
  
    -   **DirectQueryWithInMemory**  
  
  
