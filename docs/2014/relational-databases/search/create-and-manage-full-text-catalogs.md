---
title: Erstellen und Verwalten von Volltextkatalogen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- full-text catalogs [SQL Server], creating
- full-text search [SQL Server], using SQL Server Management Studio
ms.assetid: 824b7131-44a6-4815-89e6-62b7bab060e3
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d3d1bf94e65ffb789204bb774ea502ef824659ff
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37266326"
---
# <a name="create-and-manage-full-text-catalogs"></a>Erstellen und Verwalten von Volltextkatalogen
  Ein Volltextkatalog ist ein virtuelles Objekt, das keiner Dateigruppe angehört. Es ist ein logisches Konzept, das für eine Gruppe von Volltextindizes steht.  
  
##  <a name="creating"></a> Erstellen eines Volltextkatalogs  
  
#### <a name="to-create-a-full-text-catalog"></a>So erstellen Sie einen Volltextkatalog  
  
1.  Erweitern Sie im Objekt-Explorer den Server, erweitern Sie **Datenbanken**, und erweitern Sie die Datenbank, in der der Volltextkatalog erstellt werden soll.  
  
2.  Erweitern Sie **Speicher**, und klicken Sie dann mit der rechten Maustaste auf **Volltextkataloge**.  
  
3.  Wählen Sie **Neuer Volltextkatalog**aus.  
  
4.  Geben Sie im Dialogfeld **Neuer Volltextkatalog** die Informationen für den erneut zu erstellenden Volltextkatalog an. Weitere Informationen finden Sie unter [Neuer Volltextkatalog &#40;Seite „Allgemein“&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).  
  
    > [!NOTE]  
    >  Volltextkatalog-IDs beginnen bei 00005 und werden mit jedem neu erstellten Katalog um eins erhöht.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
  
##  <a name="props"></a> Anzeigen der Eigenschaften eines Volltextkatalogs  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] Funktionen, z. B. FULLTEXTCATALOGPROPERTY können verwendet werden, um den Wert verschiedener Eigenschaften, die im Zusammenhang mit der Volltextindizierung abzurufen. Diese Informationen sind für die Verwaltung und Problembehandlung der Volltextsuche hilfreich.  
  
 In der folgenden Tabelle sind die Eigenschaften aufgeführt, die sich auf Volltextkataloge beziehen.  
  
|Eigenschaft|Description|Funktion|  
|--------------|-----------------|--------------|  
|`AccentSensitivity`|Einstellung für die Unterscheidung nach Akzent.|[FULLTEXTCATALOGPROPERTY](/sql/t-sql/functions/fulltextcatalogproperty-transact-sql)|  
|`ImportStatus`|Gibt an, ob der Volltextkatalog importiert wird.|FULLTEXTCATALOGPROPERTY|  
|`IndexSize`|Größe des Volltextkatalogs in Megabytes (MB).|FULLTEXTCATALOGPROPERTY|  
|`ItemCount`|Aktuelle Anzahl der volltextindizierten Objekte im Volltextkatalog.|FULLTEXTCATALOGPROPERTY|  
|`MergeStatus`|Gibt an, ob eine Masterzusammenführung ausgeführt wird.|FULLTEXTCATALOGPROPERTY|  
|`PopulateCompletionAge`|Anzahl von Sekunden, die zwischen dem 01.01.1990, 00:00:00 Uhr, und der Beendigung des letzten Auffüllens des Volltextindex verstrichen sind.|FULLTEXTCATALOGPROPERTY|  
|`PopulateStatus`|Gibt den Auffüllungsstatus an.<br /><br /> [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|FULLTEXTCATALOGPROPERTY|  
|`UniqueKeyCount`|Anzahl der eindeutigen Schlüssel im Volltextkatalog.|FULLTEXTCATALOGPROPERTY|  
  
  
  
##  <a name="rebuildone"></a> Erneutes Erstellen eines Volltextkatalogs  
  
#### <a name="to-rebuild-a-full-text-catalog"></a>So erstellen Sie einen Volltextkatalog erneut  
  
1.  Erweitern Sie im Objekt-Explorer den Server, erweitern Sie **Datenbanken**, und erweitern Sie die Datenbank, die den erneut zu erstellenden Volltextkatalog enthält.  
  
2.  Erweitern Sie **Speicher**und dann **Volltextkataloge**.  
  
3.  Klicken Sie mit der rechten Maustaste auf den Namen des erneut zu erstellenden Volltextkatalogs, und wählen Sie **Neu erstellen**aus.  
  
4.  Klicken Sie auf die Frage **Möchten Sie den Volltextkatalog löschen und neu erstellen?** auf **OK**.  
  
5.  Klicken Sie im Dialogfeld **Volltextkatalog neu erstellen** auf **Schließen**.  
  
  
  
##  <a name="rebuildall"></a> Erneutes Erstellen aller Volltextkataloge für eine Datenbank  
  
#### <a name="to-rebuild-the-full-text-catalogs-for-a-database"></a>So erstellen Sie die Volltextkataloge für eine Datenbank erneut  
  
1.  Erweitern Sie im Objekt-Explorer den Server, erweitern Sie **Datenbanken**, und erweitern Sie die Datenbank, die die erneut zu erstellenden Volltextkataloge enthält.  
  
2.  Erweitern Sie **Speicher**, und klicken Sie dann mit der rechten Maustaste auf **Volltextkataloge**.  
  
3.  Wählen Sie **Alle neu erstellen**aus.  
  
4.  Klicken Sie bei der Frage **Möchten Sie alle Volltextkataloge löschen und neu erstellen?** auf die Option **OK**.  
  
5.  Klicken Sie im Dialogfeld **Alle Volltextkataloge neu erstellen** auf **Schließen**.  
  
  
  
##  <a name="removing"></a> Entfernen eines Volltextkatalogs aus einer Datenbank  
  
#### <a name="to-remove-a-full-text-catalog-from-a-database"></a>So entfernen Sie einen Volltextkatalog aus einer Datenbank  
  
1.  Erweitern Sie im Objekt-Explorer den Server, erweitern Sie **Datenbanken**, und erweitern Sie die Datenbank, die den zu entfernenden Volltextkatalog enthält.  
  
2.  Erweitern Sie **Speicher**und dann **Volltextkataloge**.  
  
3.  Klicken Sie mit der rechten Maustaste auf den zu entfernenden Katalog, und wählen Sie dann **Löschen**aus.  
  
4.  Klicken Sie im Dialogfeld **Objekte löschen** auf **OK**.  
  
  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql)  
  
  
