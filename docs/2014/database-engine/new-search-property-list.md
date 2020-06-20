---
title: Neue Such Eigenschaften Liste | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.newsearchpropertylist.f1
ms.assetid: ffca78e9-8608-4b15-bd38-b2d78da4247a
author: rothja
ms.author: jroth
ms.openlocfilehash: 48c9e475b380d5f0c7310e33717f261c38acbbd4
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84930371"
---
# <a name="new-search-property-list"></a>Neue Sucheigenschaftenliste
  In diesem Dialogfeld können Sie eine Sucheigenschaftenliste erstellen.  
  
## <a name="options"></a>Tastatur  
 **Name der Sucheigenschaftenliste**  
 Geben Sie den Namen der Sucheigenschaftenliste ein.  
  
 **Besitzer**  
 Geben Sie den Besitzer der Sucheigenschaftenliste an. Wenn Sie sich selbst, d. h. den aktuellen Benutzer, als Besitzer angeben möchten, lassen Sie dieses Feld leer. Klicken Sie auf die Schaltfläche zum Durchsuchen, um einen anderen Benutzer auszuwählen.  
  
### <a name="create-search-property-list-options"></a>Optionen zum Erstellen von Sucheigenschaftenlisten  
 Klicken Sie auf eine der folgenden Optionen:  
  
 **Erstellen einer leeren Sucheigenschaftenliste**  
 Erstellt eine Sucheigenschaftenliste ohne Eigenschaften.  
  
 **Von einer vorhandenen Sucheigenschaftenliste erstellen**  
 Kopiert die Eigenschaften aus einer vorhandenen Sucheigenschaftenliste in die neue Eigenschaftenliste. Sucheigenschaftenlisten bilden Datenbankobjekte, deshalb müssen Sie die Datenbank angeben, die die zu kopierende Eigenschaftenliste enthält.  
  
 **Quelldatenbank**  
 Geben Sie den Namen der Datenbank an, zu der die vorhandene Sucheigenschaftenliste gehört. Standardmäßig ist die aktuelle Datenbank ausgewählt. Wenn die aktuelle Verbindung einer Benutzer-ID in dieser Datenbank zugeordnet ist, können Sie im Listenfeld optional eine andere Datenbank auswählen.  
  
 **Quelle für Sucheigenschaftenliste**  
 Wählen Sie in den zur ausgewählten Datenbank gehörenden Listen den Namen einer vorhandenen Sucheigenschaftenliste aus.  
  
## <a name="permissions"></a>Berechtigungen  
 Weitere Informationen finden Sie unter [Create Search Property List &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql).  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a>So verwalten Sie Sucheigenschaftenlisten in SQL Server Management Studio  
 Informationen zum Erstellen, Anzeigen, Ändern oder Löschen einer Sucheigenschaftenliste und zum Konfigurieren eines Volltextindexes für die Eigenschaftensuche finden Sie unter [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Such Eigenschaften Liste &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql)   
 [Durchsuchen von Dokumenteigenschaften mithilfe von Such Eigenschaften Listen](../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  
