---
title: Benutzerdefinierte Keystore-Anbieter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a6166d7d-ef34-4f87-bd1b-838d3ca59ae7
ms.author: v-chojas
manager: jroth
author: MightyPen
ms.openlocfilehash: 84e729cd60a28ff8a58760bd3810ec538a327007
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800490"
---
# <a name="custom-keystore-providers"></a>Benutzerdefinierte Keystore-Anbieter
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="overview"></a>Übersicht

Die Spalte Verschlüsselungsfunktion von SQL Server 2016 erfordert, dass der verschlüsselte Spaltenverschlüsselungsschlüssel (ECEKs) auf dem Server gespeichert werden vom Client abgerufen und anschließend entschlüsselt, Verschlüsselung von Spaltenverschlüsselungsschlüsseln (CEKs), um die in verschlüsselten Spalten gespeicherten Daten zuzugreifen. ECEKs werden von Spaltenhauptschlüsseln (CMKs) verschlüsselt, und die Sicherheit der CMK ist wichtig, die Sicherheit der spaltenverschlüsselung. Daher sollten die CMK an einem sicheren Ort gespeichert werden. eine Spalte Verschlüsselung Keystore-Anbieter dient zur Verfügung zu stellen eine Schnittstelle für den ODBC-Treiber sicher auf diese zugreifen können CMKs gespeichert. Für Benutzer mit dem ihre eigenen sicheren Speicher bietet die benutzerdefinierte Keystore-Anbieter-Schnittstelle ein Framework für die Implementierung der Zugriff auf Speicher, der den CMK für den ODBC-Treiber zu schützen, das auszuführenden CEK Ver- und Entschlüsselung verwendet werden kann.

Jeder Keystore-Anbieter enthält, und verwaltet eine oder mehrere CMKs, der durch Schlüsselpfade - Zeichenfolgen in einem Format identifiziert werden, die vom Anbieter definiert. Dies kann zusammen mit der Verschlüsselungsalgorithmus, der auch eine Zeichenfolge, die vom Anbieter definiert, führen Sie die Verschlüsselung von ein CEK und die Entschlüsselung von einem ECEK verwendet werden. Der Algorithmus, zusammen mit ECEK und den Namen des Anbieters, werden in Metadaten der Datenbank gespeichert; finden Sie unter [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) und [CREATE COLUMN ENCRYPTION KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md) für Weitere Informationen. Daher sind die zwei grundlegende Vorgänge der schlüsselverwaltung eingehen:

```
CEK = DecryptViaCEKeystoreProvider(CEKeystoreProvider_name, Key_path, Key_algorithm, ECEK)

-and-

ECEK = EncryptViaCEKeystoreProvider(CEKeyStoreProvider_name, Key_path, Key_algorithm, CEK)
```

in denen die `CEKeystoreProvider_name` wird verwendet, um den bestimmten Spalte Verschlüsselung Keystore-Anbieter (CEKeystoreProvider), und die anderen Argumente werden von der CEKeystoreProvider zum Verschlüsseln/Entschlüsseln des CEK (E) verwendet. Den Namen und einen Schlüsselpfad werden durch die CMK-Metadaten bereitgestellt, während dem Algorithmus und ECEK-Wert von den CEK-Metadaten bereitgestellt werden. Mehrere Keystore-Anbieter können zusammen mit der integrierten Standard-Anbieter vorhanden sein. Beim Ausführen eines Vorgangs den CEK erfordert, der Treiber verwendet den CMK-Metadaten, um anhand des Namens des entsprechenden Keystore-Anbieters zu ermitteln, und führt die entschlüsselt werden, als ausgedrückt werden kann:

```
CEK = CEKeyStoreProvider_specific_decrypt(Key_path, Key_algorithm, ECEK)
```

Obwohl der Treiber nicht erforderlich, verschlüsseln CEKs aufweist, müssen möglicherweise ein Verwaltungstool, um Vorgänge wie z. B. CMK erstellen und Rotieren implementieren; Dies erfordert, der umgekehrten Vorgang ausgeführt:

```
ECEK = CEKeyStoreProvider_specific_encrypt(Key_path, Key_algorithm, CEK)
```

### <a name="cekeystoreprovider-interface"></a>CEKeyStoreProvider-Schnittstelle

Dieses Dokument beschreibt ausführlich die CEKeyStoreProvider-Schnittstelle. Ein Keystore-Anbieter, der diese Schnittstelle implementiert wird, kann der Microsoft ODBC-Treiber für SQL Server verwendet werden. Dieses Handbuch können CEKeyStoreProvider Implementierer weiterentwickeln, indem Sie den Treiber benutzerdefinierte Keystore-Anbieter verwendet werden.

Eine Keystore-Anbieterbibliothek ("die Anbieterbibliothek") ist eine Dynamic Link Library die vom ODBC-Treiber geladen werden kann, und enthält eine oder mehrere Keystore-Anbieter. Das Symbol `CEKeystoreProvider` muss von einer Anbieterbibliothek exportiert werden, und die Adresse der eine mit Null endendes Array von Zeigern auf `CEKeystoreProvider` Strukturen, eine für jeden Keystore-Anbieter in der Bibliothek.

Ein `CEKeystoreProvider` Struktur definiert die Einstiegspunkte eines einzelnen Keystore-Anbieters:

```
typedef struct CEKeystoreProvider {
    wchar_t *Name;
    int (*Init)(CEKEYSTORECONTEXT *ctx, errFunc *onError);
    int (*Read)(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int *len);
    int (*Write)(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int len);
    int (*DecryptCEK)(  CEKEYSTORECONTEXT *ctx,
                        errFunc *onError,
                        const wchar_t *keyPath,
                        const wchar_t *alg,
                        unsigned char *ecek,
                        unsigned short ecekLen,
                        unsigned char **cekOut,
                        unsigned short *cekLen);
    int (*EncryptCEK)(  CEKEYSTORECONTEXT *ctx,
                        errFunc *onError,
                        const wchar_t *keyPath,
                        const wchar_t *alg,
                        unsigned char *cek,
                        unsigned short cekLen,
                        unsigned char **ecekOut,
                        unsigned short *ecekLen);
    void (*Free)();
} CEKEYSTOREPROVIDER;
```

|Feldname|und Beschreibung|
|:--|:--|
|`Name`|Der Name des Keystore-Anbieters. Sie müssen nicht identisch mit anderen Keystore-Anbieter, zuvor geladen wird, vom Treiber oder in dieser Bibliothek vorhanden sein. Auf NULL endende Zeichenfolge für breite* Zeichen.|
|`Init`|Die Initialisierungsfunktion. Wenn Sie keine Initialisierungsfunktion nicht erforderlich ist, kann dieses Feld null sein.|
|`Read`|Anbieter read-Funktion. Möglicherweise null, wenn nicht erforderlich.|
|`Write`|Anbieter "Write"-Funktion. Erforderlich, wenn das Lesen nicht null ist. Möglicherweise null, wenn nicht erforderlich.|
|`DecryptCEK`|ECEK Entschlüsselung-Funktion. Diese Funktion ist der Grund für das Vorhandensein einer Keystore-Anbieter und darf nicht null sein.|
|`EncryptCEK`|CEK-Verschlüsselungsfunktion. Der Treiber ruft diese Funktion nicht, aber sie wird von schlüsselverwaltungstools ermöglichen den programmgesteuerten Zugriff auf die Erstellung von ECEK bereitgestellt. Möglicherweise null, wenn nicht erforderlich.|
|`Free`|Beendigungsfunktion. Möglicherweise null, wenn nicht erforderlich.|

Mit Ausnahme von Free, haben die Funktionen in dieser Schnittstelle, die alle ein Paar von Parametern, **Ctx** und **OnError**. Die erste gibt den Kontext, in dem die Funktion aufgerufen wird, während die zweite, zum Melden von Fehlern verwendet wird. Finden Sie unter [Kontexten](#context-association) und [Fehlerbehandlung](#error-handling) unten Weitere Informationen.

```
int Init(CEKEYSTORECONTEXT *ctx, errFunc onError);
```
Platzhaltername für eine Anbieter definierte Initialisierungsfunktion. Der Treiber ruft diese Funktion einmal ein, nachdem ein Anbieter geladen wurde, aber vor dem ersten Zeit, die sie zum Ausführen von ECEK-Entschlüsselung oder Read()/Write() benötigt anfordert. Verwenden Sie diese Funktion Initialisierungen, die es benötigt. 

|Argument|und Beschreibung|
|:--|:--|
|`ctx`|[Eingabe] Der Vorgangskontext.|
|`onError`|[Eingabe] Fehlerberichterstattungs-Funktion.|
|`Return Value`|Erfolg oder NULL, um das Fehlschlagen anzugeben ungleich NULL zurückgeben.|

```
int Read(CEKEYSTORECONTEXT *ctx, errFunc onError, void *data, unsigned int *len);
```

Platzhaltername für eine Kommunikation Anbieter definierte Funktion. Der Treiber ruft diese Funktion auf, wenn die Anwendung, die zum Lesen von Daten von einem (zuvor geschriebenen-in) Anbieter mit dem Attribut SQL_COPT_SS_CEKEYSTOREDATA Verbindung, die Anwendung zum Lesen beliebiger Daten vom Anbieter anfordert. Finden Sie unter [Kommunikation mit einer Keystore-Anbieter](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#communicating-with-keystore-providers) für Weitere Informationen.

|Argument|und Beschreibung|
|:--|:--|
|`ctx`|[Eingabe] Der Vorgangskontext.|
|`onError`|[Eingabe] Fehlerberichterstattungs-Funktion.|
|`data`|[Ausgabe] Zeiger auf einen Puffer, in dem der Anbieter von der Anwendung zu lesenden Daten schreibt. Dies entspricht dem Datenfeld der CEKEYSTOREDATA-Struktur.|
|`len`|[InOut] Zeiger auf einen Längenwert; Bei Eingabe, ist dies die maximale Länge des Datenpuffers und der Anbieter muss nicht geschrieben werden mehr als * Len Bytes darauf. Bei der Rückgabe sollte der Anbieter aktualisieren * Len mit der Anzahl der tatsächlich geschriebenen Bytes.|
|`Return Value`|Erfolg oder NULL, um das Fehlschlagen anzugeben ungleich NULL zurückgeben.|

```
int Write(CEKEYSTORECONTEXT *ctx, errFunc onError, void *data, unsigned int len);
```
Platzhaltername für eine Kommunikation Anbieter definierte Funktion. Der Treiber ruft diese Funktion auf, wenn die Anwendung, zum Schreiben von Daten an einen Anbieter mit dem Attribut SQL_COPT_SS_CEKEYSTOREDATA Verbindung anfordert, die Anwendung, der beliebige Daten an den Anbieter zu schreiben. Finden Sie unter [Kommunikation mit einer Keystore-Anbieter](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#communicating-with-keystore-providers) für Weitere Informationen.

|Argument|und Beschreibung|
|:--|:--|
|`ctx`|[Eingabe] Der Vorgangskontext.|
|`onError`|[Eingabe] Fehlerberichterstattungs-Funktion.|
|`data`|[Eingabe] Zeiger auf einen Puffer mit den Daten für den Anbieter zu lesen. Dies entspricht dem Datenfeld der CEKEYSTOREDATA-Struktur. Der Anbieter muss nicht mehr als Len Bytes aus diesen Puffer gelesen.|
|`len`|[Eingabe] Die Anzahl der Bytes, die in Daten zur Verfügung. Dies entspricht dem Feld "DataSize" der CEKEYSTOREDATA-Struktur.|
|`Return Value`|Erfolg oder NULL, um das Fehlschlagen anzugeben ungleich NULL zurückgeben.|

```
int (*DecryptCEK)( CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg, unsigned char *ecek, unsigned short ecekLen, unsigned char **cekOut, unsigned short *cekLen);
```
Platzhaltername für eine Funktion der Anbieter definierte ECEK-Entschlüsselung. Der Treiber ruft diese Funktion zum Entschlüsseln einer ECEK durch einen CMK, die diesem Anbieter zugeordnet sind, in einen CEK verschlüsselt.

|Argument|und Beschreibung|
|:--|:--|
|`ctx`|[Eingabe] Der Vorgangskontext.|
|`onError`|[Eingabe] Fehlerberichterstattungs-Funktion.|
|`keyPath`|[Eingabe] Der Wert des der [KEY_PATH](../../t-sql/statements/create-column-master-key-transact-sql.md) Metadatenattribut für den CMK auf die angegebenen ECEK verweist. Auf NULL endende Zeichenfolge für breite* Zeichen. Dies dient zum Identifizieren eines CMK von diesem Anbieter verarbeitet.|
|`alg`|[Eingabe] Der Wert des der [Algorithmus](../../t-sql/statements/create-column-encryption-key-transact-sql.md) Metadatenattribut für den angegebenen ECEK. Auf NULL endende Zeichenfolge für breite* Zeichen. Dies dient zur Identifizierung des Verschlüsselungsalgorithmus, der zum Verschlüsseln des angegebenen ECEK.|
|`ecek`|[Eingabe] Zeiger auf die ECEK entschlüsselt werden.|
|`ecekLen`|[Eingabe] Die Länge von ECEK.|
|`cekOut`|[Ausgabe] Der Anbieter sollte entschlüsselter ECEK Arbeitsspeicher zuweisen und die Adresse in der Zeiger verweist CekOut schreiben. Es muss möglich sein, diesen Block der using-Arbeitsspeicher freigeben der [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree) (Windows) oder (Linux/Mac)-Funktion freigeben. Der Anbieter sollte festlegen, war nicht genügend Arbeitsspeicher zugeordneten aufgrund eines Fehlers oder auf andere, * CekOut auf einen null-Zeiger.|
|`cekLen`|[Ausgabe] Der Anbieter sollte an die Adresse, die auf CekLen zeigt die Länge des entschlüsselter ECEK, die in der es geschrieben hat schreiben ** CekOut.|
|`Return Value`|Erfolg oder NULL, um das Fehlschlagen anzugeben ungleich NULL zurückgeben.|

```
int (*EncryptCEK)( CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg, unsigned char *cek,unsigned short cekLen, unsigned char **ecekOut, unsigned short *ecekLen);
```
Platzhaltername für eine Funktion der Anbieter definierte CEK-Verschlüsselung. Der Treiber nicht mit dieser Funktion wird noch seine Funktionalität über die ODBC-Schnittstelle verfügbar zu machen, aber sie wird von schlüsselverwaltungstools ermöglichen den programmgesteuerten Zugriff auf die Erstellung von ECEK bereitgestellt.

|Argument|und Beschreibung|
|:--|:--|
|`ctx`|[Eingabe] Der Vorgangskontext.|
|`onError`|[Eingabe] Fehlerberichterstattungs-Funktion.|
|`keyPath`|[Eingabe] Der Wert des der [KEY_PATH](../../t-sql/statements/create-column-master-key-transact-sql.md) Metadatenattribut für den CMK auf die angegebenen ECEK verweist. Auf NULL endende Zeichenfolge für breite* Zeichen. Dies dient zum Identifizieren eines CMK von diesem Anbieter verarbeitet.|
|`alg`|[Eingabe] Der Wert des der [Algorithmus](../../t-sql/statements/create-column-encryption-key-transact-sql.md) Metadatenattribut für den angegebenen ECEK. Auf NULL endende Zeichenfolge für breite* Zeichen. Dies dient zur Identifizierung des Verschlüsselungsalgorithmus, der zum Verschlüsseln des angegebenen ECEK.|
|`cek`|[Eingabe] Zeiger auf den CEK verschlüsselt werden.|
|`cekLen`|[Eingabe] Die Länge des CEK.|
|`ecekOut`|[Ausgabe] Der Anbieter muss von Arbeitsspeicher für den verschlüsselten CEK und seine Adresse in der Zeiger verweist EcekOut schreiben. Es muss möglich sein, diesen Block der using-Arbeitsspeicher freigeben der [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree) (Windows) oder (Linux/Mac)-Funktion freigeben. Der Anbieter sollte festlegen, war nicht genügend Arbeitsspeicher zugeordneten aufgrund eines Fehlers oder auf andere, * EcekOut auf einen null-Zeiger.|
|`ecekLen`|[Ausgabe] Der Anbieter sollte an die Adresse, die auf EcekLen zeigt die Länge des verschlüsselten CEK, die in der es geschrieben hat schreiben ** EcekOut.|
|`Return Value`|Erfolg oder NULL, um das Fehlschlagen anzugeben ungleich NULL zurückgeben.|

```
void (*Free)();
```
Platzhaltername für einen Anbieter definierte Beendigungsfunktion. Der Treiber kann diese Funktion bei normaler Beendigung des Prozesses aufgerufen werden.

> [!NOTE]
> *Breitzeichen-Zeichenfolgen sind 2-Byte-Zeichen (UTF-16) aufgrund, wie Sie SQL Server speichert.*


### <a name="error-handling"></a>Fehlerbehandlung

Als Fehler während der Verarbeitung von eines Anbieters auftreten können, ist ein Mechanismus bereitgestellt, um es zum Melden von Fehlern zurück an den Treiber in spezifischere Details als eine boolesche Erfolg/Fehler zu ermöglichen. Viele der Funktionen haben ein Paar von Parametern, **Ctx** und **OnError**, die für diesen Zweck zusätzlich zu den Rückgabewert von Erfolg/Fehler zusammen verwendet werden.

Die **Ctx** Parameter identifiziert den Kontext, in dem ein Anbietervorgang auftritt.

Die **OnError** Parameter verweist auf eine fehlerberichterstattungs-Funktion, mit dem folgenden Prototyp:

`typedef void errFunc(CEKEYSTORECONTEXT *ctx, const wchar_t *msg, ...);`

|Argument|und Beschreibung|
|:--|:--|
|`ctx`|[Eingabe] Der Kontext, der auf den Fehler zu melden.|
|`msg`|[Eingabe] Der zu meldende Fehlermeldung. Auf NULL endende Zeichenfolge für breite* Zeichen. Damit parametrisierte Informationen vorhanden sein kann, darf diese Zeichenfolge einfügen Formatieren von Sequenzen des Formulars von akzeptiert die [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage) Funktion. Erweiterte Funktionalität kann durch diesen Parameter angegeben werden, wie unten beschrieben.|
|...|[Eingabe] Zusätzliche Variadic-Parameter, die Formatbezeichner in der Meldung, nach Bedarf anpassen.|

Um zu melden, wenn ein Fehler aufgetreten ist, wird vom Treiber und eine Fehlermeldung mit optionalen zusätzlichen Parametern, die es formatiert werden der Anbieter ruft OnError, Angeben des Context-Parameters an die anbieterfunktion übergeben. Der Anbieter kann diese Funktion mehrmals aufrufen, mehrere Fehler innerhalb einer Anbieter-Funktionsaufruf fortlaufend zu übermitteln. Beispiel:

```
    if (!doSomething(...))
    {
        onError(ctx, L"An error occurred in doSomething.");
        onError(ctx, L"Additional error message with more details.");
        return 0;
    }
```


Die `msg` -Parameter ist normalerweise eine Zeichenfolge mit Breitzeichen, aber zusätzliche Erweiterungen sind verfügbar:

Mithilfe einer der speziellen vordefinierte Werte mit dem Makro IDS_MSG generische Fehlermeldungen, die bereits vorhandenen und in Form von lokalisierten im Treiber kann genutzt werden. Beispielsweise wenn ein Anbieter ein Fehler auftritt, bei der speicherbelegung die `IDS_S1_001` "Speicherbelegungsfehlers" Nachricht kann verwendet werden:

`onError(ctx, IDS_MSG(IDS_S1_001));`

Für den Fehler, die vom Treiber anerkannt werden muss der Dienstanbieter-Funktion Fehler zurückgeben. Wenn dies im Rahmen einer ODBC-Vorgang ausgeführt wird, werden die bereitgestellte Fehler zugegriffen werden kann, auf den Ziehpunkt-Verbindung oder die Anweisung über den ODBC-Diagnose Standardmechanismus, (`SQLError`, `SQLGetDiagRec`, und `SQLGetDiagField`).


### <a name="context-association"></a>Kontext-Zuordnung

Die `CEKEYSTORECONTEXT` Struktur, die zusätzlich zur Bereitstellung von Kontext für den Fehlerrückruf kann auch verwendet werden, um den ODBC-Kontext zu ermitteln, in dem ein Anbietervorgang ausgeführt wird. Dies ermöglicht einen Anbieter für die Daten aller diesen Kontexten und ordnen Sie z. B. zum Implementieren von pro-Verbindungskonfiguration. Zu diesem Zweck enthält die Struktur 3 nicht transparente Zeiger, Kontext-Umgebung, Verbindung und -Anweisung entsprechen:

```
typedef struct CEKeystoreContext
{
void *envCtx;
void *dbcCtx;
void *stmtCtx;
} CEKEYSTORECONTEXT;
```

|Feld|und Beschreibung|
|:--|:--|
|`envCtx`|Umgebungskontext.|
|`dbcCtx`|Der Verbindungskontext.|
|`stmtCtx`|Anweisungskontext.|

Jede der folgenden Kontexten ist ein nicht transparenter Wert, der beim nicht identisch mit den entsprechenden ODBC-Handle als eindeutiger Bezeichner für das Handle verwendet werden kann: Wenn behandeln *X* bezieht sich auf Kontextwert *Y*, klicken Sie dann keine andere Umgebung, Verbindung oder Anweisung Handles, die zur gleichen Zeit wie gleichzeitig vorhanden sind *X* müssen als Kontextwert *Y*, und keine anderen Kontextwerte zugeordnet werden behandeln *X*. Kontextwert in der Struktur ist null, wenn der Anbietervorgang durchgeführt wird verfügt nicht über einem bestimmtes Handle-Kontext (z. B. SQLSetConnectAttr Aufrufe zum Laden und Konfigurieren von Anbietern, in denen kein Anweisungshandle vorhanden ist) den entsprechenden.


## <a name="example"></a>Beispiel

### <a name="keystore-provider"></a>Keystore-Anbieter.

Der folgende Code ist ein Beispiel für die Implementierung eines minimalen Keystore-Anbieters.

```
/* Custom Keystore Provider Example

Windows:   compile with cl MyKSP.c /LD /MD /link /out:MyKSP.dll
Linux/Mac: compile with gcc -fshort-wchar -fPIC -o MyKSP.so -shared MyKSP.c

 */

#ifdef _WIN32
#include <windows.h>
#else
#define __stdcall
#endif

#include <stdlib.h>
#include <sqltypes.h>
#include "msodbcsql.h"
#include <sql.h>
#include <sqlext.h>

int __stdcall KeystoreInit(CEKEYSTORECONTEXT *ctx, errFunc *onError) {
    printf("KSP Init() function called\n");
    return 1;
}

static unsigned char *g_encryptKey;
static unsigned int g_encryptKeyLen;

int __stdcall KeystoreWrite(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int len) {
    printf("KSP Write() function called (%d bytes)\n", len);
    if (len) {
        if (g_encryptKey)
            free(g_encryptKey);
        g_encryptKey = malloc(len);
        if (!g_encryptKey) {
            onError(ctx, L"Memory Allocation Error");
            return 0;
        }
        memcpy(g_encryptKey, data, len);
        g_encryptKeyLen = len;
    }
    return 1;
}

// Very simple "encryption" scheme - rotating XOR with the key
int __stdcall KeystoreDecrypt(CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg,
    unsigned char *ecek, unsigned short ecekLen, unsigned char **cekOut, unsigned short *cekLen) {
    unsigned int i;
    printf("KSP Decrypt() function called (keypath=%S alg=%S ecekLen=%u)\n", keyPath, alg, ecekLen);
    if (wcscmp(keyPath, L"TheOneAndOnlyKey")) {
        onError(ctx, L"Invalid key path");
        return 0;
    }
    if (wcscmp(alg, L"none")) {
        onError(ctx, L"Invalid algorithm");
        return 0;
    }
    if (!g_encryptKey) {
        onError(ctx, L"Keystore provider not initialized with key");
        return 0;
    }
#ifndef _WIN32
    *cekOut = malloc(ecekLen);
#else
    *cekOut = LocalAlloc(LMEM_FIXED, ecekLen);
#endif
    if (!*cekOut) {
        onError(ctx, L"Memory Allocation Error");
        return 0;
    }
    *cekLen = ecekLen;
    for (i = 0; i < ecekLen; i++)
        (*cekOut)[i] = ecek[i] ^ g_encryptKey[i % g_encryptKeyLen];
    return 1;
}

// Note that in the provider interface, this function would be referenced via the CEKEYSTOREPROVIDER
// structure. However, that does not preclude keystore providers from exporting their own functions,
// as illustrated by this example where the encryption is performed via a separate function (with a
// different prototype than the one in the KSP interface.)
#ifdef _WIN32
__declspec(dllexport)
#endif
int KeystoreEncrypt(CEKEYSTORECONTEXT *ctx, errFunc *onError,
    unsigned char *cek, unsigned short cekLen,
    unsigned char **ecekOut, unsigned short *ecekLen) {
    unsigned int i;
    printf("KSP Encrypt() function called (cekLen=%u)\n", cekLen);
    if (!g_encryptKey) {
        onError(ctx, L"Keystore provider not initialized with key");
        return 0;
    }
    *ecekOut = malloc(cekLen);
    if (!*ecekOut) {
        onError(ctx, L"Memory Allocation Error");
        return 0;
    }
    *ecekLen = cekLen;
    for (i = 0; i < cekLen; i++)
        (*ecekOut)[i] = cek[i] ^ g_encryptKey[i % g_encryptKeyLen];
    return 1;
}

CEKEYSTOREPROVIDER MyCustomKSPName_desc = {
    L"MyCustomKSPName",
    KeystoreInit,
    0,
    KeystoreWrite,
    KeystoreDecrypt,
    0
};

#ifdef _WIN32
__declspec(dllexport)
#endif
CEKEYSTOREPROVIDER *CEKeystoreProvider[] = {
    &MyCustomKSPName_desc,
    0
};
```

### <a name="odbc-application"></a>ODBC-Anwendung

Der folgende Code ist eine demoanwendung, die der oben genannten Keystore-Anbieter verwendet. Wenn es ausgeführt wird, stellen Sie sicher, dass die Anbieterbibliothek in demselben Verzeichnis wie die Binärdateien der Anwendung befindet und die Verbindungszeichenfolge gibt (oder einen DSN enthält) die `ColumnEncryption=Enabled` festlegen.

```
/*
 Example application for demonstration of custom keystore provider usage

Windows:   compile with cl /MD kspapp.c /link odbc32.lib
Linux/Mac: compile with gcc -o kspapp -fshort-wchar kspapp.c -lodbc -ldl
 
 usage: kspapp connstr

 */

#define KSPNAME L"MyCustomKSPName"
#define PROV_ENCRYPT_KEY "JHKCWYT06N3RG98J0MBLG4E3"

#include <stdio.h>
#include <stdlib.h>
#ifdef _WIN32
#include <windows.h>
#else
#define __stdcall
#include <dlfcn.h>
#endif
#include <sql.h>
#include <sqlext.h>
#include "msodbcsql.h"

/* Convenience functions */

int checkRC(SQLRETURN rc, char *msg, int ret, SQLHANDLE h, SQLSMALLINT ht) {
    if (rc == SQL_ERROR) {
        fprintf(stderr, "Error occurred upon %s\n", msg);
        if (h) {
            SQLSMALLINT i = 0;
            SQLSMALLINT outlen = 0;
            char errmsg[1024];
            while ((rc = SQLGetDiagField(
                ht, h, ++i, SQL_DIAG_MESSAGE_TEXT, errmsg, sizeof(errmsg), &outlen)) == SQL_SUCCESS
                || rc == SQL_SUCCESS_WITH_INFO) {
                fprintf(stderr, "Err#%d: %s\n", i, errmsg);
            }
        }
        if (ret)
            exit(ret);
        return 0;
    }
    else if (rc == SQL_SUCCESS_WITH_INFO && h) {
        SQLSMALLINT i = 0;
        SQLSMALLINT outlen = 0;
        char errmsg[1024];
        printf("Success with info for %s:\n", msg);
        while ((rc = SQLGetDiagField(
            ht, h, ++i, SQL_DIAG_MESSAGE_TEXT, errmsg, sizeof(errmsg), &outlen)) == SQL_SUCCESS
            || rc == SQL_SUCCESS_WITH_INFO) {
            fprintf(stderr, "Msg#%d: %s\n", i, errmsg);
        }
    }
    return 1;
}

void postKspError(CEKEYSTORECONTEXT *ctx, const wchar_t *msg, ...) {
    if (msg > (wchar_t*)65535)
        wprintf(L"Provider emitted message: %s\n", msg);
    else
        wprintf(L"Provider emitted message ID %d\n", msg);
}

int main(int argc, char **argv) {
    char sqlbuf[1024];
    SQLHENV env;
    SQLHDBC dbc;
    SQLHSTMT stmt;
    SQLRETURN rc;
    unsigned char CEK[32];
    unsigned char *ECEK;
    unsigned short ECEKlen;
#ifdef _WIN32
    HMODULE hProvLib;
#else
    void *hProvLib;
#endif
    CEKEYSTORECONTEXT ctx = {0};
    CEKEYSTOREPROVIDER **ppKsp, *pKsp;
    int(__stdcall *pEncryptCEK)(CEKEYSTORECONTEXT *, errFunc *, unsigned char *, unsigned short, unsigned char **, unsigned short *);
    int i;
    if (argc < 2) {
        fprintf(stderr, "usage: kspapp connstr\n");
        return 1;
    }

    /* Load the provider library */
#ifdef _WIN32
    if (!(hProvLib = LoadLibrary("MyKSP.dll"))) {
#else
    if (!(hProvLib = dlopen("./MyKSP.so", RTLD_NOW))) {
#endif
        fprintf(stderr, "Error loading KSP library\n");
        return 2;
    }
#ifdef _WIN32
    if (!(ppKsp = (CEKEYSTOREPROVIDER**)GetProcAddress(hProvLib, "CEKeystoreProvider"))) {
#else
    if (!(ppKsp = (CEKEYSTOREPROVIDER**)dlsym(hProvLib, "CEKeystoreProvider"))) {
#endif
        fprintf(stderr, "The export CEKeystoreProvider was not found in the KSP library\n");
        return 3;
    }
    while (pKsp = *ppKsp++) {
        if (!memcmp(KSPNAME, pKsp->Name, sizeof(KSPNAME)))
            goto FoundProv;
    }
    fprintf(stderr, "Could not find provider in the library\n");
    return 4;
FoundProv:
    if (pKsp->Init && !pKsp->Init(&ctx, postKspError)) {
        fprintf(stderr, "Could not initialize provider\n");
        return 5;
    }
#ifdef _WIN32
    if (!(pEncryptCEK = (LPVOID)GetProcAddress(hProvLib, "KeystoreEncrypt"))) {
#else
    if (!(pEncryptCEK = dlsym(hProvLib, "KeystoreEncrypt"))) {
#endif
        fprintf(stderr, "The export KeystoreEncrypt was not found in the KSP library\n");
        return 6;
    }
    if (!pKsp->Write) {
        fprintf(stderr, "Provider does not support configuration\n");
        return 7;
    }

    /* Configure the provider with the key */
    if (!pKsp->Write(&ctx, postKspError, PROV_ENCRYPT_KEY, strlen(PROV_ENCRYPT_KEY))) {
        fprintf(stderr, "Error writing to KSP\n");
        return 8;
    }

    /* Generate a CEK and encrypt it with the provider */
    srand(time(0) ^ getpid());
    for (i = 0; i < sizeof(CEK); i++)
        CEK[i] = rand();

    if (!pEncryptCEK(&ctx, postKspError, CEK, sizeof(CEK), &ECEK, &ECEKlen)) {
        fprintf(stderr, "Error encrypting CEK\n");
        return 9;
    }

    /* Connect to Server */
    rc = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &env);
    checkRC(rc, "allocating environment handle", 2, 0, 0);
    rc = SQLSetEnvAttr(env, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, 0);
    checkRC(rc, "setting ODBC version to 3.0", 3, env, SQL_HANDLE_ENV);
    rc = SQLAllocHandle(SQL_HANDLE_DBC, env, &dbc);
    checkRC(rc, "allocating connection handle", 4, env, SQL_HANDLE_ENV);
    rc = SQLDriverConnect(dbc, 0, argv[1], strlen(argv[1]), NULL, 0, NULL, SQL_DRIVER_NOPROMPT);
    checkRC(rc, "connecting to data source", 5, dbc, SQL_HANDLE_DBC);
    rc = SQLAllocHandle(SQL_HANDLE_STMT, dbc, &stmt);
    checkRC(rc, "allocating statement handle", 6, dbc, SQL_HANDLE_DBC);

    /* Create a CMK definition on the server */
    {
        static char cmkSql[] = "CREATE COLUMN MASTER KEY CustomCMK WITH ("
            "KEY_STORE_PROVIDER_NAME = 'MyCustomKSPName',"
            "KEY_PATH = 'TheOneAndOnlyKey')";
        printf("Create CMK: %s\n", cmkSql);
        SQLExecDirect(stmt, cmkSql, SQL_NTS);
    }

    /* Create a CEK definition on the server */
    {
        const char cekSqlBefore[] = "CREATE COLUMN ENCRYPTION KEY CustomCEK WITH VALUES ("
            "COLUMN_MASTER_KEY = CustomCMK,"
            "ALGORITHM = 'none',"
            "ENCRYPTED_VALUE = 0x";
        char *cekSql = malloc(sizeof(cekSqlBefore) + 2 * ECEKlen + 2); /* 1 for ')', 1 for null terminator */
        strcpy(cekSql, cekSqlBefore);
        for (i = 0; i < ECEKlen; i++)
            sprintf(cekSql + sizeof(cekSqlBefore) - 1 + 2 * i, "%02x", ECEK[i]);
        strcat(cekSql, ")");
        printf("Create CEK: %s\n", cekSql);
        SQLExecDirect(stmt, cekSql, SQL_NTS);
        free(cekSql);
#ifdef _WIN32
        LocalFree(ECEK);
#else
        free(ECEK);
#endif
    }

#ifdef _WIN32
    FreeLibrary(hProvLib);
#else
    dlclose(hProvLib);
#endif

    /* Create a table with encrypted columns */
    {
        static char *tableSql = "CREATE TABLE CustomKSPTestTable ("
            "c1 int,"
            "c2 varchar(255) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = CustomCEK, ENCRYPTION_TYPE = DETERMINISTIC, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'))";
        printf("Create table: %s\n", tableSql);
        SQLExecDirect(stmt, tableSql, SQL_NTS);
    }

    /* Load provider into the ODBC Driver and configure it */
    {
        unsigned char ksd[sizeof(CEKEYSTOREDATA) + sizeof(PROV_ENCRYPT_KEY) - 1];
        CEKEYSTOREDATA *pKsd = (CEKEYSTOREDATA*)ksd;
        pKsd->name = L"MyCustomKSPName";
        pKsd->dataSize = sizeof(PROV_ENCRYPT_KEY) - 1;
        memcpy(pKsd->data, PROV_ENCRYPT_KEY, sizeof(PROV_ENCRYPT_KEY) - 1);
#ifdef _WIN32
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREPROVIDER, "MyKSP.dll", SQL_NTS);
#else
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREPROVIDER, "./MyKSP.so", SQL_NTS);
#endif
        checkRC(rc, "Loading KSP into ODBC Driver", 7, dbc, SQL_HANDLE_DBC);
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREDATA, (SQLPOINTER)pKsd, SQL_IS_POINTER);
        checkRC(rc, "Configuring the KSP", 7, dbc, SQL_HANDLE_DBC);
    }

    /* Insert some data */
    {
        int c1;
        char c2[256];
        rc = SQLBindParameter(stmt, 1, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 0, 0, &c1, 0, 0);
        checkRC(rc, "Binding parameters for insert", 9, stmt, SQL_HANDLE_STMT);
        rc = SQLBindParameter(stmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_VARCHAR, 255, 0, c2, 255, 0);
        checkRC(rc, "Binding parameters for insert", 9, stmt, SQL_HANDLE_STMT);
        for (i = 0; i < 10; i++) {
            c1 = i * 10 + i + 1;
            sprintf(c2, "Sample data %d for column 2", i);
            rc = SQLExecDirect(stmt, "INSERT INTO CustomKSPTestTable (c1, c2) values (?, ?)", SQL_NTS);
            checkRC(rc, "Inserting rows query", 10, stmt, SQL_HANDLE_STMT);
        }
        printf("(Encrypted) data has been inserted into the [CustomKSPTestTable]. You may inspect the data now.\n"
            "Press Enter to continue...\n");
        getchar();
    }

    /* Retrieve the data */
    {
        int c1;
        char c2[256];
        rc = SQLBindCol(stmt, 1, SQL_C_LONG, &c1, 0, 0);
        checkRC(rc, "Binding columns for select", 11, stmt, SQL_HANDLE_STMT);
        rc = SQLBindCol(stmt, 2, SQL_C_CHAR, c2, sizeof(c2), 0);
        checkRC(rc, "Binding columns for select", 11, stmt, SQL_HANDLE_STMT);
        rc = SQLExecDirect(stmt, "SELECT c1, c2 FROM CustomKSPTestTable", SQL_NTS);
        checkRC(rc, "Retrieving rows query", 12, stmt, SQL_HANDLE_STMT);
        while (SQL_SUCCESS == (rc = SQLFetch(stmt)))
            printf("Retrieved data: c1=%d c2=%s\n", c1, c2);
        SQLFreeStmt(stmt, SQL_CLOSE);
        printf("Press Enter to clean up and exit...\n");
        getchar();
    }

    /* Clean up */
    {
        SQLExecDirect(stmt, "DROP TABLE CustomKSPTestTable", SQL_NTS);
        SQLExecDirect(stmt, "DROP COLUMN ENCRYPTION KEY CustomCEK", SQL_NTS);
        SQLExecDirect(stmt, "DROP COLUMN MASTER KEY CustomCMK", SQL_NTS);
        printf("Removed table, CEK, and CMK\n");
    }
    SQLDisconnect(dbc);
    SQLFreeHandle(SQL_HANDLE_DBC, dbc);
    SQLFreeHandle(SQL_HANDLE_ENV, env);
    return 0;
}

```

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Always Encrypted mit dem ODBC-Treiber](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
