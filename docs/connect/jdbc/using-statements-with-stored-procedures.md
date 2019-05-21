---
title: Verwenden von Anweisungen mit gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0041f9e1-09b6-4487-b052-afd636c8e89a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d12b5d0940ea161e3650dc5126a10783c1afc3e6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47812848"
---
# <a name="using-statements-with-stored-procedures"></a>Verwenden von Anweisungen mit gespeicherten Prozeduren

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Bei einer gespeicherten Prozedur handelt es sich um eine Datenbankprozedur, ähnlich einer Prozedur in anderen Programmiersprachen, die in der eigentlichen Datenbank enthalten ist. In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können gespeicherte Prozeduren mit [!INCLUDE[tsql](../../includes/tsql-md.md)] oder mit der Common Language Runtime (CLR) und einer der Visual Studio-Programmiersprachen wie Visual Basic oder C# erstellt werden. Im Allgemeinen weisen gespeicherte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozeduren die folgenden Merkmale auf:  
  
- Annehmen von Eingabeparametern und Zurückgeben mehrerer Werte in Form von Ausgabeparametern an die aufrufende Prozedur oder den aufrufenden Batch.  
  
- Aufnehmen von Programmierungsanweisungen, die Operationen in der Datenbank ausführen, einschließlich des Aufrufens anderer Prozeduren.  
  
- Zurückgeben eines Statuswertes an eine aufrufende Prozedur oder einen aufrufenden Batch, der Erfolg oder Fehlschlagen (sowie die Ursache für das Fehlschlagen) anzeigt.  
  
> [!NOTE]  
> Weitere Informationen zu gespeicherten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozeduren finden Sie unter „Grundlegendes zu gespeicherten Prozeduren“ in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
Zum Verarbeiten von Daten in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank mit einer gespeicherten Prozedur verfügt [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] über die Klassen [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) und [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Welche Klasse verwendet wird, hängt davon ab, ob von der gespeicherten Prozedur IN- (Eingabe) oder OUT-Parameter (Ausgabe) benötigt werden. Wenn die gespeicherte Prozedur keine IN- oder OUT-Parameter benötigt, können Sie die SQLServerStatement-Klasse verwenden. Wenn die gespeicherte Prozedur mehrmals aufgerufen wird oder nur IN-Parameter benötigt, können Sie die SQLServerPreparedStatement-Klasse verwenden. Wenn die gespeicherte Prozedur erfordert in- und OUT-Parameter, Sie sollten die SQLServerCallableStatement-Klasse verwenden. Nur wenn die gespeicherte Prozedur OUT-Parameter benötigt, müssen Sie den Aufwand für die Verwendung der SQLServerCallableStatement-Klasse betreiben.  
  
> [!NOTE]  
> Gespeicherte Prozeduren können auch Updatezählungen und mehrere Resultsets zurückgeben. Weitere Informationen finden Sie unter [mithilfe einer gespeicherten Prozedur mit einer Updatezählung](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md) und [mehrere Resultsets mithilfe von](../../connect/jdbc/using-multiple-result-sets.md).  
  
Wenn Sie den JDBC-Treiber verwenden, um eine gespeicherte Prozedur mit Parametern aufzurufen, müssen Sie die `call`-SQL-Escapesequenz zusammen mit der [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)-Methode der [SQLServerConnection-Klasse](../../connect/jdbc/reference/sqlserverconnection-class.md) verwenden. Die vollständige Syntax für die `call`-Escapesequenz lautet wie folgt:  
  
 `{[?=]call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
> Weitere Informationen zu den `call` und anderen SQL-Escapesequenzen, finden Sie unter [mithilfe von SQL-Escapesequenzen](../../connect/jdbc/using-sql-escape-sequences.md).  
  
Die Themen in diesem Abschnitt beschreiben, wie Sie gespeicherte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Prozeduren mit dem JDBC-Treiber und der`call`-SQL-Escapesequenz aufrufen können.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Beschreibung|  
|-----------|-----------------|  
|[Verwenden von gespeicherten Prozeduren ohne Parameter](../../connect/jdbc/using-a-stored-procedure-with-no-parameters.md)|Beschreibt die Verwendung des JDBC-Treibers zum Ausführen von gespeicherten Prozeduren, die keine Eingabe- oder Ausgabeparameter enthalten.|  
|[Verwenden von gespeicherten Prozeduren mit Eingabeparametern](../../connect/jdbc/using-a-stored-procedure-with-input-parameters.md)|Beschreibt die Verwendung des JDBC-Treibers zum Ausführen von gespeicherten Prozeduren, die Eingabeparameter enthalten.|  
|[Verwenden von gespeicherten Prozeduren mit Ausgabeparametern](../../connect/jdbc/using-a-stored-procedure-with-output-parameters.md)|Beschreibt die Verwendung des JDBC-Treibers zum Ausführen von gespeicherten Prozeduren, die Ausgabeparameter enthalten.|  
|[Verwenden von gespeicherten Prozeduren mit einem Rückgabestatus](../../connect/jdbc/using-a-stored-procedure-with-a-return-status.md)|Beschreibt die Verwendung des JDBC-Treibers zum Ausführen von gespeicherten Prozeduren, die Rückgabestatuswerte enthalten.|  
|[Verwenden von gespeicherten Prozeduren mit einer Updatezählung](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md)|Beschreibt die Verwendung des JDBC-Treibers zum Ausführen von gespeicherten Prozeduren, die Updatezählungen enthalten.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Verwenden von Anweisungen mit dem JDBC-Treiber](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
