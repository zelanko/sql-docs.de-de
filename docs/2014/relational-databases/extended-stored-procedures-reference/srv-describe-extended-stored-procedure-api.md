---
title: srv_describe (API für die erweiterte gespeicherte Prozedur) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_describe
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_describe
ms.assetid: 2115600e-5ce7-4be0-9cd3-a1dd1fab0729
author: rothja
ms.author: jroth
ms.openlocfilehash: 264781f21e328c4740ee31b53fe3812bbe392305
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050782"
---
# <a name="srv_describe-extended-stored-procedure-api"></a>srv_describe (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Definiert den Spaltennamen und die Quellen- und Zieldatentypen für eine bestimmte Spalte in einer Zeile.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
int srv_describe (  
SRV_PROC *  
srvproc  
,  
int  
colnumber  
,  
DBCHAR *  
column_name  
,  
int  
namelen  
,  
DBINT  
desttype  
,  
DBINT  
destlen  
,  
DBINT  
srctype  
,  
DBINT  
srclen  
,  
void *  
srcdata  
);  
  
```  
  
## <a name="arguments"></a>Argumente  
 *srvproc*  
 Ist ein Zeiger auf die SRV_PROC-Struktur, die das Handle für eine bestimmte Clientverbindung ist (in diesem Fall der die Zeile sendende Client). Die Struktur enthält alle Kontrollinformationen, mit der die API-Bibliothek für erweiterte gespeicherte Prozeduren Kommunikationen und Daten zwischen der Anwendung und dem Client verwaltet.  
  
 *colnumber*  
 Wird derzeit nicht unterstützt. Spalten müssen der Reihe nach beschrieben werden. Alle Spalten müssen vor dem Aufrufen von **srv_sendrow** beschrieben werden.  
  
 *column_name*  
 Gibt den Namen der Spalte an, zu der die Daten gehören. Dieser Parameter kann NULL sein, da eine Spalte nicht zwingend einen Namen haben muss.  
  
 *namelen*  
 Gibt die Länge von *column_name* in Byte an. Wenn *namelen* den Wert SRV_NULLTERM hat, muss *column_name* NULL-terminiert sein.  
  
 *desttype*  
 Gibt den Datentyp der Spalte mit der Zielzeile an. Dies ist der Datentyp, der an den Client gesendet wird. Der Datentyp muss angegeben werden, auch wenn die Daten NULL sind. Weitere Informationen finden Sie unter [Data Types (Extended Stored Procedure API) (Datentypen (API für erweiterte gespeicherte Prozeduren))](data-types-extended-stored-procedure-api.md).  
  
 *destlen*  
 Gibt die Länge der Daten in Byte an, die an den Client gesendet werden sollen. Für Datentypen mit fester Länge, die keine NULL-Werte zulassen, wird *destlen* ignoriert. Für Datentypen variabler Länge und Datentypen fester Länge, die NULL-Werte zulassen, gibt *destlen* die maximal zulässige Länge der Zieldaten an.  
  
 *srctype*  
 Gibt den Datentyp der Quelldaten an.  
  
 *srclen*  
 Gibt die Länge der Quelldaten in Byte an. Dieser Wert wird für Datentypen fester Länge ignoriert.  
  
 *srcdata*  
 Stellt die Quelldatenadresse für eine bestimmte Spalte zur Verfügung. Wenn **srv_sendrow** aufgerufen wird, werden die Daten für *colnumber* in *srcdata* gesucht. Daher sollte keine Freigabe vor einem Aufruf von **srv_sendrow** erfolgen. Die Quelldatenadresse kann zwischen Aufrufen von **srv_sendrow** mit **srv_setcoldata** geändert werden. Der *srcdata* zugewiesene Speicher sollte erst freigegeben werden, bis die Spaltendaten durch einen anderen Aufruf von **srv_setcoldata** ersetzt wurden oder bis **srv_senddone** aufgerufen wird.  
  
 Wenn *desttype* den Wert SRVDECIMAL oder SRVNUMERIC aufweist, muss der *srcdata*-Parameter ein Zeiger auf eine DBNUMERIC- oder DBDECIMAL-Struktur sein, und die Felder für Genauigkeit und Dezimalstellen müssen bereits auf die gewünschten Werte festgelegt worden sein. Mit DEFAULTPRECISION können Sie eine Standardgenauigkeit angeben und mit DEFAULTSCALE einen Standardwert für die Dezimalstellen.  
  
## <a name="returns"></a>Gibt zurück  
 Die Nummer der beschriebenen Spalte. Die erste Spalte ist die Spalte 1. Tritt ein Fehler auf, wird 0 zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die **srv_describe**-Funktion muss einmal für jede Spalte in der Zeile aufgerufen werden, bevor der erste Aufruf von **srv_sendrow** erfolgt. Die Spalten einer Zeile können in jeder Reihenfolge beschrieben werden.  
  
 Verwenden Sie **srv_setcoldata** bzw. **srv_setcollen**, um den Speicherort und die Länge der Quelldaten in Spaltenzeilen zu ändern, bevor das gesamte Resultset gesendet wurde.  
  
 Eine Beschreibung von Datentypen und Datentypkonvertierungen der API für erweiterte gespeicherte Prozeduren finden Sie unter [Data Types (Extended Stored Procedure API) (Datentypen (API für erweiterte gespeicherte Prozeduren))](data-types-extended-stored-procedure-api.md).  
  
 Wenn der Spaltenname in der Anwendung in Unicode angegeben ist, muss er in die Multibytecodepage des Servers konvertiert werden, bevor **srv_describe** aufgerufen wird. Weitere Informationen finden Sie unter [Unicode-Daten und Server-Codepages](../extended-stored-procedures-programming/unicode-data-and-server-code-pages.md).  
  
> [!IMPORTANT]  
>  Sie sollten den Quellcode der erweiterten gespeicherten Prozeduren sorgfältig prüfen, und Sie sollten die kompilierten DLL-Dateien testen, bevor Sie sie auf einem Produktionsserver installieren. Weitere Informationen zum Überprüfen und Testen der Sicherheit finden Sie auf dieser [Microsoft-Website](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>Weitere Informationen  
 [srv_sendrow &#40;API für erweiterte gespeicherte Prozeduren&#41;](srv-sendrow-extended-stored-procedure-api.md)   
 [srv_setutype &#40;API für erweiterte gespeicherte Prozeduren&#41;](srv-setutype-extended-stored-procedure-api.md)   
 [srv_setcoldata (API für erweiterte gespeicherte Prozeduren)](srv-setcoldata-extended-stored-procedure-api.md)  
  
  
