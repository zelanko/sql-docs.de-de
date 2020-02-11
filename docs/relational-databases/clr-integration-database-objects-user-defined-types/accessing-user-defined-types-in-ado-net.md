---
title: Zugreifen auf benutzerdefinierte Typen in ADO.net | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
author: rothja
ms.author: jroth
ms.openlocfilehash: b4bdbf184cc1528b3eb5156173f52dca44aece76
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68009610"
---
# <a name="accessing-user-defined-types-in-adonet"></a>Zugreifen auf benutzerdefinierte Typen in ADO.NET
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Benutzerdefinierte Typen (User-Defined Types, UDTs) werden mit einer beliebigen Sprache geschrieben [!INCLUDE[msCoName](../../includes/msconame-md.md)] , die von der .NET Framework Common Language Runtime (CLR) unterstützt wird, die überprüfbaren Code erzeugt. Dazu gehören [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# und [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic. UDTs ermöglichen das Speichern von Objekten und benutzerdefinierten Datenstrukturen in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank. Die Daten werden als öffentliche Elemente einer .NET Framework-Klasse oder -Struktur verfügbar gemacht. Das Verhalten wird durch die Methoden der Klasse oder Struktur definiert. Ein UDT kann als Spaltendefinition einer Tabelle, als Variable in einem [!INCLUDE[tsql](../../includes/tsql-md.md)]-Batch oder als Argument einer [!INCLUDE[tsql](../../includes/tsql-md.md)]-Funktion oder gespeicherten Prozedur verwendet werden.  
  
 In ADO.NET stellt der **System. Data. SqlClient** -Anbieter UDTs auf folgende Weise bereit:  
  
-   Über den **System. Data. SqlClient. SqlDataReader** als Objekt.  
  
-   Über **SqlDataReader** als Rohdaten bytes.  
  
-   Als Parameter eines **System. Data. SqlClient. SqlParameter** -Objekts.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Abrufen von UDT-Daten](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-retrieving-udt-data.md)  
 Beschreibt, wie UDT-Daten abgerufen und Parameter angegeben werden.  
  
 [Aktualisieren von UDT-Spalten mit DataAdapters](../../relational-databases/clr-integration-database-objects-user-defined-types/accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 Beschreibt das Arbeiten mit UDTs in **DataSets** und das Aktualisieren von UDT-Daten mithilfe von **DataAdapters**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerdefinierte CLR-Typen](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
  
  
