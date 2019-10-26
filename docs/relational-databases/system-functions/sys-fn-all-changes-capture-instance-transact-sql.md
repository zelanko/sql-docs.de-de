---
title: sys. fn_all_changes_&lt;capture_instance&gt; (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_all_changes
- sys.fn_all_changes
- fn_all_changes_TSQL
- sys.fn_all_changes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_all_changes_<capture_instance>
- sys.fn_all_changes_<capture_instance>
ms.assetid: 564fae96-b88c-4f22-9338-26ec168ba6f5
author: rothja
ms.author: jroth
ms.openlocfilehash: 6b9b6e62d0f69c5182ad69e21cb46800d4ddcc86
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909400"
---
# <a name="sysfn_all_changes_ltcapture_instancegt-transact-sql"></a>sys. fn_all_changes_&lt;capture_instance&gt; (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wrapper für die Abfragefunktionen **alle Änderungen** . Die zum Erstellen dieser Funktionen erforderlichen Skripts werden von der gespeicherten Prozedur sys.sp_cdc_generate_wrapper_function generiert.  
  
 ![Themen Link Symbol](../../database-engine/configure-windows/media/topic-link.gif "Link Symbol "Thema"") [Transact-SQL-Syntax Konventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn_all_changes_<capture_instance> ('start_time' ,'end_time', '<row_filter_option>' )  
  
<capture_instance> ::= The name of the capture instance.  
<row_filter_option> ::=  
{ all  
  | all update old  
}  
```  
  
## <a name="arguments"></a>Argumente  
 *start_time*  
 Der **DateTime** -Wert, der den unteren Endpunkt des Bereichs von Änderungs Tabellen Einträgen darstellt, der im Resultset enthalten sein soll.  
  
 Im Resultset sind nur Zeilen in der CDC. < capture_instance > _CT-Änderungs Tabelle enthalten, die eine zugeordnete comdtzeit aufweisen, die größer als *start_time* ist.  
  
 Wenn für dieses Argument ein Wert von NULL übergeben wird, entspricht der untere Endpunkt des Abfragebereichs dem unteren Endpunkt des gültigen Bereichs der Aufzeichnungsinstanz.  
  
 *end_time*  
 Der **DateTime** -Wert, der den hohen Endpunkt des Bereichs von Änderungs Tabellen Einträgen darstellt, der im Resultset enthalten sein soll.  
  
 Dieser Parameter kann eine von zwei möglichen Bedeutungen annehmen, abhängig von dem für @closed_high_end_point ausgewählten Wert, wenn sys. sp_cdc_generate_wrapper_function aufgerufen wird, um das CREATE-Skript für die Wrapper Funktion zu generieren:  
  
-   @closed_high_end_point = 1  
  
     Im Resultset sind nur Zeilen in der CDC. < capture_instance > _CT-Änderungs Tabelle enthalten, die eine zugeordnete comdtzeit aufweisen, die kleiner oder gleich end_time ist.  
  
-   @closed_high_end_point = 0  
  
     Im Resultset sind nur Zeilen in der Änderungs Tabelle cdc. capture_instance_CT enthalten, denen eine comdtzeit zugeordnet ist, die streng kleiner als end_time ist.  
  
 Wenn für dieses Argument ein Wert von NULL übergeben wird, entspricht der obere Endpunkt des Abfragebereichs dem oberen Endpunkt des gültigen Bereichs der Aufzeichnungsinstanz.  
  
 < row_filter_option >:: = {all | Alle aktualisieren alt}  
 Eine Option, die den Inhalt der Metadatenspalten sowie die im Resultset zurückgegebenen Zeilen bestimmt.  
  
 Eine der folgenden Optionen ist möglich:  
  
 all  
 Gibt alle Änderungen innerhalb des angegebenen LSN-Bereichs zurück. Bei Änderungen aufgrund eines Updatevorgangs gibt diese Option nur die Zeile zurück, die die neuen Werte nach Anwendung des Updates enthält.  
  
 all update old  
 Gibt alle Änderungen innerhalb des angegebenen LSN-Bereichs zurück. Bei Änderungen aufgrund eines Updatevorgangs gibt die Option die beiden Zeilen zurück, die die Spaltenwerte vor und nach dem Update enthalten.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
  
|Spaltenname|Spaltentyp|Description|  
|-----------------|-----------------|-----------------|  
|__CDC_STARTLSN|**binary(10)**|Die Commit-LSN der Transaktion, die der Änderung zugeordnet ist. Alle Änderungen, für die ein Commit in derselben Transaktion ausgeführt wurde, verwenden dieselbe Commit-LSN.|  
|__CDC_SEQVAL|**binary(10)**|Sequenzwert, mit dem Zeilenänderungen in einer Transaktion sortiert werden.|  
|Spalten aus @column_list\<|**variiert**|Die Spalten, die im *column_list* -Argument für sp_cdc_generate_wrapper_function identifiziert werden, wenn Sie aufgerufen wird, um das Skript zu generieren, mit dem die Wrapper Funktion erstellt wird.|  
|__CDC_OPERATION|**nvarchar (2)**|Ein Vorgangscode, der den Vorgang angibt, der zum Anwenden der Zeile auf die Zielumgebung erforderlich ist. Dies variiert basierend auf dem Wert des Arguments *row_filter_option* , das im-Befehl angegeben wird:<br /><br /> *row_filter_option* = ' all '<br /><br /> 'D' - Löschvorgang<br /><br /> 'I' - Einfügevorgang<br /><br /> 'UN' - Updatevorgang, neue Werte<br /><br /> *row_filter_option* = "Alle aktualisieren alt"<br /><br /> 'D' - Löschvorgang<br /><br /> 'I' - Einfügevorgang<br /><br /> 'UN' - Updatevorgang, neue Werte<br /><br /> 'UO' - Updatevorgang, alte Werte|  
|Spalten aus @update_flag_list\<|**bit**|Ein Bitflag, das durch Anfügen von _uflag an den Spaltennamen benannt wird. Das Flag wird immer auf NULL festgelegt, wenn \__CDC_OPERATION "," I ", von" uo "ist. Wenn \__CDC_OPERATION auf ' un ' festgelegt ist, wird es auf 1 festgelegt, wenn das Update eine Änderung an der entsprechenden Spalte erzeugt hat. Andernfalls ist es 0.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die Funktion "fn_all_changes_ < capture_instance >" dient als Wrapper für die Funktion "cdc. fn_cdc_get_all_changes_ < capture_instance > Query". Die gespeicherte Prozedur sys.sp_cdc_generate_wrapper wird zum Generieren des Skripts zum Erstellen des Wrappers verwendet.  
  
 Wrapperfunktionen werden nicht automatisch erstellt. Es gibt zwei Dinge, die Sie tun müssen, um Wrapper Funktionen zu erstellen:  
  
1.  Führen Sie die gespeicherte Prozedur aus, um das Skript zu generieren, das den Wrapper erstellt.  
  
2.  Führen Sie das Skript aus, das die Wrapperfunktion tatsächlich erstellt.  

 Wrapper Funktionen ermöglichen Benutzern eine systematische Abfrage von Änderungen, die in einem Intervall aufgetreten sind, das durch **DateTime** -Werte und nicht durch LSN-Werte begrenzt ist. Die Wrapper Funktionen führen alle erforderlichen Konvertierungen zwischen den angegebenen **DateTime** -Werten und den LSN-Werten aus, die intern als Argumente für die Abfragefunktionen erforderlich sind. Wenn die Wrapper Funktionen serialisiert zum Verarbeiten eines Streams von Änderungs Daten verwendet werden, stellen Sie sicher, dass keine Daten verloren gehen oder wiederholt werden, sofern die folgende Konvention befolgt wird: der @end_time Wert des Intervalls, das einem-Befehl zugeordnet ist, wird als @start_time bereitgestellt. der Wert für das Intervall, das dem nachfolgenden-Befehl zugeordnet ist.  
  
 Wenn Sie den Parameter @closed_high_end_point bei Erstellung des Skripts verwenden, können Sie Wrapper generieren, die im angegebenen Abfragefenster eine geschlossene obere Grenze oder eine offene untere Grenze unterstützen. Sie können also entscheiden, ob Einträge mit einer Commitzeit in das Intervall aufgenommen werden sollen, die der oberen Grenze des Extrahierungsintervalls entspricht. Standardmäßig wird die Obergrenze aufgenommen.  
  
 Das Resultset, das von der Wrapper Funktion **alle Änderungen** zurückgegeben wird, gibt die __ $ start_lsn-und \_\_$seqval Spalten der Änderungs Tabelle als Spalten \__CDC_STARTLSN bzw. \__CDC_SEQVAL zurück. Dabei werden nur die verfolgten Spalten befolgt, die beim Generieren des Wrappers im Parameter *\@column_list* aufgetreten sind. Wenn *\@column_list* den Wert NULL hat, werden alle nach verfolgten Quell Spalten zurückgegeben. Auf die Quell Spalten folgt eine Vorgangs Spalte, \__CDC_OPERATION, bei der es sich um eine Spalte mit einem oder zwei Zeichen handelt, die den Vorgang identifiziert.  
  
 Bitflags werden dann dem Resultset für die einzelnen Spalten angehängt, die im Parameter @update_flag_list identifiziert sind. Für den Wrapper **alle Änderungen** sind die Bitflags immer NULL, Wenn __CDC_OPERATION den Wert 'd ', ' I ' oder ' UO ' hat. Wenn \__CDC_OPERATION auf ' un ' festgelegt ist, wird das Flag auf 1 oder 0 festgelegt, je nachdem, ob der Aktualisierungs Vorgang eine Änderung an der Spalte verursacht hat.  
  
 Die Change Data Capture Konfigurations Vorlage ' Instantiate CDC Wrapper TVFs for Schema ' zeigt, wie die gespeicherte Prozedur sp_cdc_generate_wrapper_function verwendet wird, um CREATE-Skripts für alle Wrapper Funktionen für die definierten Abfragefunktionen eines Schemas abzurufen. Diese Skripts werden dann von der Vorlage erstellt. Weitere Informationen zu Vorlagen finden Sie unter [Vorlagen-Explorer](../../ssms/template/template-explorer.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [sys.sp_cdc_generate_wrapper_function &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-generate-wrapper-function-transact-sql.md)   
 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
