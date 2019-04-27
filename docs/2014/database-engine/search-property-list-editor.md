---
title: Suche plist | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.searchpropertylisteditor.f1
ms.assetid: 0f3ced6e-0dfd-49fc-b175-82378c3d668e
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 818e1176cb5a4f81205a36dc7be6fd9fded286ea
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62773668"
---
# <a name="search-property-list-editor"></a>Sucheigenschaftenlisten-Editor
  In diesem Dialogfeld können Sie einer Sucheigenschaftenliste Sucheigenschaften hinzufügen oder solche darin löschen.  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a>So verwalten Sie Sucheigenschaftenlisten in SQL Server Management Studio  
 Weitere Informationen über das Erstellen, anzeigen oder Löschen einer sucheigenschaftenliste und zum Konfigurieren einen Volltextindex für die Eigenschaftensuche finden Sie unter [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).  
  
## <a name="options"></a>Optionen  
 **Eigenschaftenname**  
 Geben Sie den Namen an, der in Volltextabfragen für die Eigenschaft verwendet werden soll. Eigenschaftsnamen können interne Leerzeichen enthalten. Die maximale Länge von **Eigenschaftsname** beträgt 256 Zeichen. Für diesen Name kann ein benutzerfreundlicher Name verwendet werden, z. B. "Autor" oder "Privatadresse", oder aber der kanonische Windows-Name der Eigenschaft, z. B. `System.Author` oder `System.Contact.HomeAddress`. **Eigenschaftsname** muss die Eigenschaft innerhalb des Eigenschaftensatzes eindeutig bezeichnen.  
  
 Entwickler bezeichnen die Eigenschaft im [CONTAINS](/sql/t-sql/queries/contains-transact-sql) -Prädikat über den Eigenschaftsnamen. Wenn Sie eine Eigenschaft hinzufügen, sollten Sie daher einen Wert angeben, mit dem die Eigenschaft aussagekräftig bezeichnet wird.  
  
 **Eigenschaftensatz-GUID**  
 Geben Sie den Bezeichner des Eigenschaftensatzes an, zu dem die Eigenschaft gehört. Bei diesem handelt es sich um einen global eindeutigen Bezeichner (GUID, Globally Unique Identifier). Als Eigenschaftensatz wird eine Gruppe logisch aufeinander bezogener Eigenschaften bezeichnet. Informationen zum Abrufen dieses Werts finden Sie weiter unten in diesem Thema unter "Hinweise".  
  
 **Ganzzahlige Eigenschafts-ID**  
 Gibt einen ganzzahligen Bezeichner für die Eigenschaft an. Dieser vorab zugewiesene Wert ist eine positive ganze Zahl, die innerhalb des Eigenschaftensatzes eindeutig ist. Informationen zum Abrufen dieses Werts finden Sie weiter unten in diesem Thema unter "Hinweise".  
  
> [!NOTE]  
>  Dokumenteigenschaften, in denen Zeichenfolgenbezeichner verwendet werden, werden von der Volltextsuche nicht unterstützt.  
  
 **Beschreibung der Eigenschaft**  
 Sie können auch eine Beschreibung der Eigenschaft angeben. Dies ist eine Zeichenfolge mit bis zu 512 Zeichen. Eine Beschreibung kann beispielsweise Informationen zum Eigenschaftensatz der Eigenschaft oder Informationen zu einer Eigenschaft enthalten, die aus deren Namen nicht hervorgehen.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie einer Sucheigenschaftenliste eine Sucheigenschaft hinzufügen möchten, müssen Sie den GUID (Globally Unique Identifier (GUID) des Eigenschaftensatzes, zu dem die Eigenschaft gehört, sowie den ganzzahligen Eigenschaftsbezeichner der Eigenschaft angeben. Jede dieser Kombinationen muss in einer einzelnen Sucheigenschaftenliste eindeutig sein. Wenn Sie versuchen, eine bereits vorhandene Kombination hinzuzufügen, tritt ein Fehler mit Fehlermeldung auf. Daher können Sie für jede Eigenschaft nur einen Namen konfigurieren.  
  
 Die Eigenschaftsbeschreibung ist optional.  
  
 **So konfigurieren Sie eine sucheigenschaftenliste für einen Volltextindex**  
  
-   [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
## <a name="permissions"></a>Berechtigungen  
 Finden Sie unter [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql).  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql)   
 [Suchen von Dokumenteigenschaften mithilfe von Sucheigenschaftenlisten](../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  
