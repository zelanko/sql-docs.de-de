---
title: Definieren von UDT-Tabellen und-Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [CLR integration], columns
- UDTs [CLR integration], columns
- columns [CLR integration]
- user-defined types [CLR integration], tables
- tables [CLR integration]
- UDTs [CLR integration], tables
- UDTs [CLR integration], indexes
- user-defined types [CLR integration], indexes
- indexes [CLR integration]
ms.assetid: aea495f4-ce26-4952-b019-38f012625f3f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1b87e497c6610a2d75daa9432246e4f4b4690bab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62874447"
---
# <a name="defining-udt-tables-and-columns"></a>Definieren von UDT-Tabellen und -Spalten
  Sobald die Assembly, die den benutzerdefinierten Typ (UDT) enthält die Definition in registriert hat eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank kann in einer Spaltendefinition verwendet werden.  
  
## <a name="creating-tables-with-udts"></a>Erstellen von Tabellen mit UDTs  
 Es gibt keine spezielle Syntax für das Erstellen einer UDT-Spalte in einer Tabelle. Sie können den Namen des UDT in einer Spaltendefinition verwenden, als wäre er einer der systeminternen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen. Die folgende CREATE TABLE- [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung erstellt eine Tabelle mit dem Namen **Punkte**, mit einer Spalte namens **-ID,** diese wird als definiert eine `int` Identity-Spalte und \ den Primärschlüssel für die Tabelle. Die zweite Spalte den Namen **PointValue**, mit dem Datentyp **Punkt**. In diesem Beispiel verwendete Schemaname ist **Dbo**. Beachten Sie, dass Sie über die erforderlichen Berechtigungen verfügen müssen, um einen Schemanamen anzugeben. Wenn Sie den Schemanamen nicht angeben, wird das Standardschema für den Datenbankbenutzer verwendet.  
  
```  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a>Erstellen von Indizes für UDT-Spalten  
 Es gibt zwei Optionen für das Indizieren einer UDT-Spalte:  
  
-   Indizieren Sie den vollständigen Wert. In diesem Fall, wenn der UDT binär sortiert ist, können Sie einen Index über die gesamte UDT-Spalte mithilfe der CREATE INDEX-[!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung erstellen.  
  
-   Indizieren Sie UDT-Ausdrücke. Sie können Indizes auf persistenten berechneten Spalten über UDT-Ausdrücken erstellen. Der UDT-Ausdruck kann ein Feld, eine Methode oder eine Eigenschaft eines UDT sein. Der Ausdruck muss deterministisch sein und darf keinen Datenzugriff ausführen.  
  
 Weitere Informationen finden Sie unter [CLR-benutzerdefinierten Typen](clr-user-defined-types.md) und [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).  
  
## <a name="see-also"></a>Siehe auch  
 [Arbeiten mit benutzerdefinierten Typen in SQL Server](working-with-user-defined-types-in-sql-server.md)  
  
  
