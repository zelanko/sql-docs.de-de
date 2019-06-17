---
title: Spalten für Volltextindex (Dialogfeld) (Visual Database Tools) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.fulltextcolumn
ms.assetid: a6f41c5c-d950-4d64-9e42-d062925917b6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8b47ec263ad22317990fd547e93a5ec3821abdb1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65105092"
---
# <a name="full-text-index-columns-dialog-box-visual-database-tools"></a>Spalten für Volltextindex (Dialogfeld) (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
In diesem Dialogfeld werden die Spalten aufgelistet, die in den Volltextindex für die im Tabellen-Designer geöffnete Tabelle einbezogen sind. Klicken Sie zum Zugreifen auf dieses Dialogfeld mit der rechten Maustaste auf die Tabelle im Tabellen-Designer, und wählen Sie **Volltextindex** aus. Klicken Sie im Dialogfeld **Volltextindex** auf den Index mit den anzuzeigenden bzw. zu bearbeitenden Spalten, klicken Sie im rechten Datenblatt auf das Feld **Spalten**, und klicken Sie auf die Auslassungspunkte ( **...** ).  
  
## <a name="options"></a>enthalten  
**Spalte**  
Zeigt die Namen der Spalten an, die in den Volltextindex einbezogen werden. Um eine Spalte hinzuzufügen, klicken Sie auf die erste leere Zelle, und wählen Sie eine Spalte aus der Dropdownliste aus. Sie können nur auf Spalten zugreifen, die textbasierte Datentypen bzw. Imagedatentypen enthalten.  
  
**Datentyp**  
Zeigt den Datentyp für jede Spalte an. Dies ist eine schreibgeschützte Eigenschaft. Öffnen Sie zum Ändern eines Datentyps die Tabelle im Tabellen-Designer, klicken Sie auf die Spalte, und bearbeiten Sie den Datentyp auf der Registerkarte **Spalteneigenschaften** .  
  
**Nach Spalte eingegeben**  
Gilt nur für Spalten mit dem Datentyp **image**. Stellt eine Dropdownliste bereit, aus der Sie auswählen können, welche anderen Spalten den Datentyp dieser Spalte darstellen. Wenn diese Spalte nicht den Datentyp **image** aufweist, wird der Wert „None“ verwendet.  
  
Spalten mit dem Datentyp **image** können Microsoft Office-Dateien (DOC-, XLS- und PPT-Dateien), Textdateien (TXT-Dateien) sowie HTML-Dateien (HTM-Dateien) enthalten. Wenn der Datentyp für die Spalte auf „image“ festgelegt wird, kann der Inhalt der Dateien bei der Volltextsuche durchsucht werden.  
  
**Sprache**  
Listet verfügbare Sprachen auf. Wählen Sie aus der Dropdownliste die für die Spaltendaten entsprechende Sprache aus. Wenn Sie beispielsweise ein Betriebssystem in englischer Sprache verwenden, jedoch eine Spalte indizieren möchten, die deutschen Text enthält, wählen Sie aus der Dropdownliste Deutsch aus, um die Leistung des Index zu verbessern.  
  
**Statistische Semantik**  
Wählen Sie aus, ob die semantische Indizierung für die ausgewählte Spalte aktiviert werden soll. Weitere Informationen finden Sie unter [Semantische Suche](https://msdn.microsoft.com/cd8faa9d-07db-420d-93f4-a2ea7c974b97).  
  
Wenn Sie eine **Sprache** vor der Option **Statistische Semantik**auswählen und die ausgewählte Sprache über kein zugeordnetes semantisches Sprachmodell verfügt, ist das Kontrollkästchen **Statistische Semantik** deaktiviert. Wenn Sie **Statistische Semantik** vor einer **Sprache**auswählen, werden im Dropdown-Kombinationsfeld nur die Sprachen angezeigt, für die das semantische Sprachmodell unterstützt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
[Volltextindex (Dialogfeld) &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/full-text-index-dialog-box-visual-database-tools.md)  
  
