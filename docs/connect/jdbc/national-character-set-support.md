---
title: Unterstützung für nationale Zeichensätze | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4fceacfd-df4f-40cd-b7a2-5e5e58a5979f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3ceb2d12ba3d062b3ba592eb6baa93fe93223907
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80912216"
---
# <a name="national-character-set-support"></a>Unterstützung für nationale Zeichensätze
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Der JDBC-Treiber bietet Unterstützung für die JDBC 4.0-API, die neue API-Methoden für die Konvertierung nationaler Zeichensätze enthält. Diese Unterstützung umfasst neue Setter-, Getter-und Updatermethoden für die JDBC-Typen **NCHAR**, **NVARCHAR**, **LONGNVARCHAR** und **NCLOB**.  
  
 In der folgenden Liste sind die Methoden zum Abrufen, Festlegen und Aktualisieren für die Unterstützung der Konvertierung nationaler Zeichensätze aufgeführt:  
  
-   [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md): [setNString](../../connect/jdbc/reference/setnstring-method-int-java-lang-string.md), [setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlserverpreparedstatement.md), [setNClob](../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md).  
  
-   [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md): [getNClob](../../connect/jdbc/reference/getnclob-method-sqlservercallablestatement.md), [getNString](../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md), [getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlservercallablestatement.md), [setNString](../../connect/jdbc/reference/setnstring-method-sqlservercallablestatement.md), [setNCharacterStream](../../connect/jdbc/reference/setncharacterstream-method-sqlservercallablestatement.md), [setNClob](../../connect/jdbc/reference/setnclob-method-sqlservercallablestatement.md).  
  
-   [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md): [getNClob](../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md), [getNString](../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md), [getNCharacterStream](../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md), [updateNClob](../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md), [updateNString](../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md), [updateNCharacterStream](../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md).  
  
> [!NOTE]  
>  Um diese Methoden in einer Anwendung verwenden zu können, müssen Sie den Klassenpfad so festlegen, dass die Datei sqljdbc.jar enthalten ist.  
  
 Damit String-Parameter im Unicode-Format an den Server gesendet werden, sollten die Anwendungen entweder die neuen JDBC 4.0-Methoden für nationale Zeichensätze verwenden oder die **sendStringParametersAsUnicode**-Verbindungseigenschaft auf „**true**“ festlegen, wenn die Methoden für nicht nationale Zeichensätze verwendet werden. Es wird empfohlen, nach Möglichkeit die neuen JDBC 4.0-Methoden für nationale Zeichensätze zu verwenden. Weitere Informationen zur **sendStringParametersAsUnicode**-Verbindungseigenschaft finden Sie unter [Festlegen von Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu den Datentypen des JDBC-Treibers](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
