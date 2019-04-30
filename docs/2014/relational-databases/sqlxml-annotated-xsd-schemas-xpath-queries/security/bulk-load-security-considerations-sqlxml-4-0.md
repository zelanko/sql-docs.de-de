---
title: Massenimport von Sicherheitsüberlegungen (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- bulk load [SQLXML], security
- security [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], security
ms.assetid: 192fc6d4-ecbc-4a4d-a5cb-55e1f64af318
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a3c304302f17c360dd9bb3a0ac51c7ea50bce40d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63268660"
---
# <a name="bulk-load-security-considerations-sqlxml-40"></a>Sicherheitsüberlegungen zum Massenladen (SQLXML 4.0)
  Im Folgenden finden Sie Sicherheitsrichtlinien zur Verwendung zum XML-Massenladen:  
  
-   Wenn Sie angeben, dass ein Massenladevorgang als Transaktion ausgeführt werden soll, geben Sie über die `TempFilePath`-Eigenschaft den Ordner an, in dem temporäre Dateien erstellt werden sollen.  
  
     Während des Massenladevorgangs werden diese temporären Dateien mit den folgenden Berechtigungen erstellt:  
  
    -   Dem Massenladevorgang wird Lese-, Schreib- und Löschzugriff gewährt.  
  
    -   Alle Benutzer erhalten Leseberechtigungen, weil nicht bekannt ist, unter welchem Konto Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf diese Dateien zugreifen wird. Sie können den Zugriff auf diese temporären Dateien einschränken, indem Sie für den Ordner, in dem sie enthalten sind, die gewünschten Berechtigungen festlegen.  
  
-   Für das XML-Massenladen selbst sind keine Berechtigungseinstellungen verfügbar. Es wird vorausgesetzt, das die Datenbank korrekt eingerichtet wurde und dass für den Benutzerkontext (d. h. den Anmeldenamen, der zum Massenladen verwendet wird) die geeigneten Berechtigungen festgelegt wurden.  
  
-   Wenn während eines Massenladevorgangs, der nicht im Transaktionsmodus ausgeführt wird, ein Fehler auftritt, dann bleiben Daten möglicherweise in einem teilweise geladenen Zustand. Wenn ein Fehler in diesem Modus auftritt, wird der Massenladevorgang einfach angehalten. Durch die Verwendung des Transaktionsmodus lässt sich dieses Problem beheben.  
  
-   Wenn Fehler beim Massenladen auftreten, enthalten sie möglicherweise Informationen über die Datenbank. Zum Beispiel können sie den Namen einer Tabelle oder einer Spalte oder Informationen zum Spaltentyp umfassen. Beim Einsatz des Massenladens sollten Sie dafür sorgen, dass Fehler im Massenladevorgang abgefangen werden und dass eine allgemeine Fehlermeldung ausgegeben wird, statt Fehler für die Benutzer direkt verfügbar zu machen.  
  
-   Beim Massenladen unterliegt die zu verarbeitende Datenmenge keiner Beschränkung. Beim Massenladen wird die Größe der Daten, die geladen werden sollen, nicht überprüft. Es liegt in der Verantwortung des Benutzers, der das Massenladen ausführt, sicherzustellen, dass ausreichend Speicher zum Verarbeiten der angegebenen Datei und ausreichend Platz in der Datenbank zum Speichern der geladenen Daten verfügbar ist.  
  
-   Beim Massenladen wird nicht versucht, die als Code übergebenen Daten zu verwenden. Die Dateneingabe wird nie in irgendeiner Weise ausgeführt. In der Eingabe enthaltener Code oder Befehle werden wie normale Daten behandelt und nicht ausgeführt.  
  
-   Beim Massenladen können Formatierungsänderungen an den angegebenen Daten basierend auf den Unterschieden zwischen dem XML- und dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenmodell vorgenommen werden. Zum Beispiel ist das Format für die Zeitangabe unterschiedlich. Beim Massenladen wird versucht, diese Unterschiede aufzulösen. Als Folge können Genauigkeitsinformationen verloren gehen.  
  
-   Beim Massenladen gelten keine Beschränkungen hinsichtlich der Datenverarbeitungsdauer. Die Verarbeitung wird fortgesetzt, bis die Verarbeitung abgeschlossen ist oder ein Fehler auftritt.  
  
-   Beim Massenladen können temporäre Tabellen innerhalb der Datenbank erstellt und gelöscht werden, und daher benötigt der Prozess hierfür entsprechende Berechtigungen. Die Berechtigungen für diese Tabellen werden dem Benutzer erteilt, der für den Massenladeprozess eine Verbindung mit der Datenbank herstellt.  
  
-   Beim Massenladen können temporäre Dateien, die während der Verarbeitung im Transaktionsmodus verwendet werden, erstellt und gelöscht werden, und daher benötigt der Prozess hierfür entsprechende Berechtigungen. Diese Dateien werden mit den gleichen Berechtigungen erstellt, über die der Benutzer des Threads verfügt, in dem der Massenladevorgang ausgeführt wird.  
  
-   Wenn der Benutzer eine Fehlerprotokolldatei festlegt, in die SQLXML Fehler ausgeben soll, dann wird diese Datei bei jeder Ausführung des Massenladevorgangs mit den Daten aus dem letzten Massenladeprozess überschrieben.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführen von Massenladen von XML-Daten &#40;SQLXML 4.0&#41;](../bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  
