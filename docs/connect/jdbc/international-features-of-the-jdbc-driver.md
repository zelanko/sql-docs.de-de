---
title: Internationale Features des JDBC-Treibers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: bbb74a1d-9278-401f-9530-7b5f45aa79de
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f02c3aecda4c4d346b72c236156dd2b250ef63a2
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924675"
---
# <a name="international-features-of-the-jdbc-driver"></a>Internationale Funktionen des JDBC-Treibers
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Die Internationalisierungsfeatures von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] umfassen Folgendes:  
  
-   Unterstützung einer vollständigen Lokalisierung in den gleichen Sprachen wie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Unterstützung für Java-Sprachumwandlungen für gebietsschemasensitive [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Daten  
  
-   Betriebssystemunabhängige Unterstützung internationaler Sprachen  
  
-   Unterstützung für internationale Domänennamen (beginnend mit Microsoft JDBC-Treiber 6.0 für SQL Server)  
  
## <a name="handling-of-character-data"></a>Verarbeitung von Zeichendaten  
 Zeichendaten in Java werden standardmäßig als Unicode-Daten verarbeitet; das Java-Objekt **String** stellt Unicode-Zeichendaten dar. Die einzige Ausnahme dieser Regel im JDBC-Treiber bilden die Abruf- und Festlegungsmethoden für ASCII-Datenströme. Dabei handelt es sich um Sonderfälle, da Bytedatenströme mit der impliziten Voraussetzung einer einzelnen bekannten Codepage (ASCII) verwendet werden.  
  
 Darüber hinaus stellt der JDBC-Treiber die -Verbindungszeichenfolgeeigenschaft **sendStringParametersAsUnicode** bereit. Mit dieser Eigenschaft kann angegeben werden, dass die vorbereiteten Parameter für Zeichendaten anstatt in Unicode in ASCII oder als Multibyte-Zeichensatz (MBCS) gesendet werden. Weitere Informationen zur Verbindungszeichenfolgeneigenschaft **sendStringParametersAsUnicode** finden Sie unter [Festlegen von Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md).  
  
### <a name="driver-incoming-conversions"></a>Konvertierung eingehender Daten  
 Unicode-Textdaten vom Server brauchen nicht konvertiert zu werden. Sie werden direkt als Unicode-Daten übergeben. Nicht-Unicode-Daten vom Server werden von der Codepage für die Daten auf Datenbank- oder Spaltenebene in Unicode konvertiert. Der JDBC-Treiber verwendet die JVM-Konvertierungsroutinen (Java Virtual Machine) für diese Konvertierungen. Diese Konvertierungen werden in allen Abrufmethoden für typisierte Zeichenfolge- und Zeichendatenströme ausgeführt.  
  
 Wenn die JVM nicht die richtige Codepage für die Daten aus der Datenbank unterstützt, löst der JDBC-Treiber die Ausnahme "Codepage XXX wird von der Java-Umgebung nicht unterstützt." aus. Zum Beheben dieses Problems sollten Sie die vollständige Unterstützung für internationale Zeichensätze installieren, die für diese JVM erforderlich ist. Ein Beispiel finden Sie auf der Sun Microsystems-Website in der Dokumentation zu unterstützten Codierungen.  
  
### <a name="driver-outgoing-conversions"></a>Konvertierung ausgehender Daten  
 Zeichendaten vom Treiber zum Server können als ASCII oder Unicode übertragen werden. Die neuen JDBC 4.0-Methoden für nationale Zeichensätze wie „setNString“, „setNCharacterStream“ und „setNClob“ der Klassen [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) und [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) senden ihre Parameterwerte immer im Unicode-Format an den Server.  
  
 Die API-Methoden für nicht nationale Zeichensätze wie „setString“, „setCharacterStream“ und „setClob“ der Klassen [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) und [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) senden ihre Werte hingegen nur im Unicode-Format an den Server, wenn die Eigenschaft **sendStringParametersAsUnicode** auf TRUE festgelegt ist, was dem Standardwert entspricht.  
  
## <a name="non-unicode-parameters"></a>Nicht-Unicode-Parameter  
 Um bei Verwendung der folgenden Typen von Nicht-Unicode-Parametern eine optimale Leistung zu erhalten, legen Sie die**sendStringParametersAsUnicode**-Verbindungszeichenfolgeneigenschaft auf FALSE fest und verwenden die Methoden für nicht nationale Zeichen: **CHAR**, **VARCHAR** oder **LONGVARCHAR**.  
  
## <a name="formatting-issues"></a>Formatierungsprobleme  
 Bei Datums-, Uhrzeit- und Währungsangaben erfolgt die gesamte Formatierung mit lokalisierten Daten mit dem Locale-Objekt und den verschiedenen Formatierungsmethoden für die Datentypen **Date**, **Calendar** und **Number** auf Java-Ebene. In den seltenen Fällen, in denen der JDBC-Treiber gebietsschemasensitive Daten in einem lokalisierten Format übergeben muss, wird die entsprechende Formatierungsmethode mit dem JVM-Standardgebietsschema verwendet.  
  
## <a name="collation-support"></a>Unterstützung für Sortierungen  
 Der JDBC-Treiber 3.0 unterstützt alle Sortierungen, die von [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und den in [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] eingeführten neuen Sortierungen bzw. neuen Versionen der Windows-Sortierungsnamen unterstützt werden.  
  
 Weitere Informationen zu Sortierungen finden Sie unter [Collation and Unicode Support (Sortierung und Unicode-Unterstützung)](https://go.microsoft.com/fwlink/?LinkId=131366) und [Name der Windows-Sortierung (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=131367) in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="using-international-domain-names-idn"></a>Verwendung internationaler Domänennamen (IDN)  
 Der JDBC-Treiber 6.0 für SQL Server unterstützt die Verwendung internationaler Domänennamen (IDNs) und kann bei Bedarf während einer Verbindung einen Unicode-Servernamen in ASCII-kompatible Codierung (Punycode) konvertieren.  Wenn die IDNs im Domain Name System (DNS) als ASCII-Zeichenfolgen im Punycode-Format (angegeben durch RFC 3490) gespeichert sind, aktivieren Sie die Konvertierung der Unicode-ServerName, indem Sie die ServerNameAsACE-Eigenschaft auf „true“ setzen.  Wenn der DNS-Dienst für die Verwendung von Unicode-Zeichen konfiguriert ist, setzen Sie die ServerNameAsACE-Eigenschaft auf „false“ (Standard).  Bei älteren Versionen des JDBC-Treibers können Sie den Servernamen in Punycode konvertieren, indem Sie die [IDN.toASCII-Methoden von Java](https://docs.oracle.com/javase/8/docs/api/java/net/IDN.html) verwenden, bevor Sie die Eigenschaft für eine Verbindung festlegen.  
  
> [!NOTE]  
>  Der Großteil der für Windows-Plattformen geschriebenen Konfliktlösersoftware basiert auf den Internet-DSN-Standards und verwendet aus diesem Grund mit hoher Wahrscheinlichkeit das Punycode-Format für IDN. Ein Windows-basierter DNS-Server in einem privaten Netzwerk kann hingegen so konfiguriert werden, dass die Verwendung von UTF-8-Zeichen auf Serverbasis möglich ist.  Weitere Informationen finden Sie unter [Unicode character support (Unterstützung von Unicode-Zeichen)](https://technet.microsoft.com/library/cc738403(v=ws.10).aspx).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über den JDBC-Treiber](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
