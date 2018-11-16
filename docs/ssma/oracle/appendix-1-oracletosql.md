---
title: Anhang – 1 (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e01f8be5-ce68-4c9f-bd13-d65e73a16470
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 2539ac90fcce2dd1d5b30384c07bac620d809f0a
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51668239"
---
# <a name="appendix---1-oracletosql"></a>Anhang – 1 (OracleToSQL)
Schnelle Übersicht über die Befehlszeilenoptionen von SSMA-Konsole:  
  
|Sl. Nein.|Schalter|Erforderlich?|Switch-Argument|Zulässige Werte|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|Benutzerkontensteuerung|scriptfile|XML-Dateiname ist ungültig.<br /><br />Definition des Skriptdatei-Konsole.|  
|2|-V/variable|nein|variablevaluefile|XML-Dateiname ist ungültig.<br /><br />Wenn die Variable im Skriptdatei verwendet werden, muss diese Datei angegeben werden.|  
|3|-c/serverconnection|nein|serverconnectionfile|XML-Dateiname ist ungültig.<br /><br />Diese Datei enthält die Verbindungsinformationen.|  
|4|-X / Xmloutput|nein|xmloutputfile|Diese Option gibt die Ausgabe im XML-Format in der Konsole an. Wenn diese Option nicht angegeben ist, wird die standardmäßigen Ausgabe im Textformat.<br /><br />Wenn Xmloutputfile nicht angegeben ist, wird der XML-Ausgabe zu geleitet `STDOUT`.<br /><br />Xmloutputfile ist der Name der Datei in der die Ausgabe der Konsole in der XML-Format geschrieben wird.|  
|5|-l/log|nein|logfile|Der Dateiname ist ungültig.|  
|6|-e/projectenvironment|nein|projectenvironmentfolder|Gültigen Ordnernamen ein, die Dateien der SSMA-Projekt enthält.|  
|7|-p/securepassword|nein|-a/hinzufügen {< Server_id > [,... n] &#124; alle} – C&#124;Serverconnection < Server-Verbindung-File > [-V&#124;Variable < Variable-Wert-File >] [-o/overwrite]<br /><br />oder<br /><br />-a/hinzufügen {< Server_id > [,... n] &#124; alle} – s&#124;Skript < Script-File > [-V&#124;Variable < Variable-Wert-File >] [-o/overwrite]<br /><br />-r/Remove {< Server_id > [,... n] &#124; alle}<br /><br />-l/Auflisten<br /><br />– e/Export {< Server-Id > [,... n] &#124; alle} < verschlüsselt – Kennwort - Datei ><br /><br />– i / import {< Server-Id > [,... n] &#124; alle} < verschlüsselt-Kennwort-File >|Wenn angegeben, muss diese Option nicht mit anderen Optionen kombiniert werden.<br /><br />Server-Id: eine eindeutige ID für einen Server {String} bereitgestellt<br /><br />Server-Connection-Datei: Server-Definitionsdatei (Serverconnectionfile oder Scriptfile).<br /><br />Variable-Wert-Datei: Dabei handelt es sich eine Variablendefinition-Datei, die in Server-Connection-Datei verwendet.<br /><br />verschlüsselten Kennwortdatei: Es ist eine Server-Kennwörter-Datei mit einer benutzerdefinierten-Passphrase verschlüsselt.|  
|8|-?|nein|Nicht zutreffend|Nicht zutreffend|  
  
## <a name="see-also"></a>Siehe auch  
[Executing the SSMA Console ausführen (Oracle)](https://msdn.microsoft.com/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
