# AT.NetCore.Common
In the programming world the developers must have to note some common functions/methods into somewhere in mind or maintain notebook. 
This AT.NetCore.Common library provides those kind of common functions/methods and it reduces 30% developers coding time. I am not saying that AT.NetCore.Common libary has provided very extensive methods. In fact, the small methods that are regularly useful in our day-to-day coding.

# Nuget Package
[![NuGet version (AT.NetCore.Common)](https://img.shields.io/nuget/v/AT.NetCore.Common.svg?style=flat-square)](https://www.nuget.org/packages/AT.NetCore.Common/)


###### AT.NetCore.Common has following namespaces underwhich static classes are defined.
```
1. AT.NetCore.Common
	└ PubliceProcedures
2. AT.NetCore.Common.Extension
	├ Data
	├ Date
	├ Enum
	└ String
3. AT.NetCore.Common.Cryptography
	├ Text
	└ File
4. AT.NetCore.Common.Serialization
	├ JSON
	└ XML
```

## In Detail

**1. AT.NetCore.Common.PublicProcedures**

This class contains the useful properties and method to serve the helpful functionality to enhance and reduce the coding efforts. 

**Method:**
```
/// <summary>
/// Static method to get the public/external IP address.
/// <param name="errorMessage">Provide error message holding parameter.</param>
/// </summary>
/// <returns></returns>
string GetIPAddress(ref string errorMessage)

/// <summary>
/// Static method returns the list of timezones.
/// </summary>
/// <returns></returns>
ReadOnlyCollection<TimeZoneInfo> GetTimezones()

/// <summary>
/// Static method returns the list of timezones async.
/// </summary>
/// <returns></returns>
async Task<ReadOnlyCollection<TimeZoneInfo>> GetTimezonesAsync()

/// <summary>
/// Static method to convert the currency into words.
/// </summary>
/// <param name="number">Provide amount</param>
/// <param name="currency">Provide currency name</param>
/// <param name="monetaryUnit">Provide monetary unity name</param>
/// <exception cref="ArgumentEmptyException"></exception>
/// <exception cref="InvaildNumberStringException"></exception>
/// <returns></returns>
string ConvertCurrencyToWords(string number, string currency = "Rupees", string monetaryUnit = "Paisa")

/// <summary>
/// Static method to convert number into words.
/// </summary>
/// <param name="number">Provide number.</param>
/// <returns></returns>
/// <exception cref="ArgumentEmptyException"></exception>
string ConvertNumberToWords(string number)

/// <summary>
/// Static method generates the GUID string.
/// </summary>
/// <returns></returns>
string GenerateGUID(GUIDExtraction extraction = GUIDExtraction.AlphaNumbers, int? length = 10)

/// <summary>
/// Static method to read the excel file and return data in table form.
/// </summary>
/// <param name="path">Provide the excel sheet file.</param> 
/// <param name="sheetName">Provide the sheetname</param>
/// <param name="hasHeader">Provide the boolean value to check the sheet has first row as header or not.</param>
/// <returns></returns>
/// <exception cref="FilePathEmptyException"></exception>
/// <exception cref="FileNotFoundException"></exception>
/// <exception cref="SheetnameEmptyException"></exception>
DataTable ReadExcelToTable(string path, string sheetName, bool hasHeader = true)

/// <summary>
/// Static method to get the permutation numbers of sum check value.
///<para>sumCheckValue is the addition of any combination of 2^n. Here n is 1,2,3,4,5,6,.....n </para>
/// </summary>
/// <param name="sumCheckValue">Provide the sum check value.</param>
/// <returns></returns>
List<long> GetPermutation(long sumCheckValue)

/// <summary>
/// Static method to check the credit card number is valid or invalid.
/// </summary>
/// <param name="cardNumber"></param>
/// <returns></returns>
bool IsValidPaymentCardNumber(string cardNumber)

```

**2. AT.NetCore.Common.Extension**

**Data:**
```
/// Extension method to compare the two object and return boolean value.
obj.EqualTo(toCompare)
  
/// Extension method to check the object is blank or not.
obj.IsBlank();

/// Extension method to create the structural clone of object.
obj.CreateClone<T>();

/// Extension method to convert generic object into bytes.
obj.ToBytes<T>();

/// Extension method that map/convert the bytes data into the specified generic type.
byte[].ToObject<T>();

/// Extension Method to map the object.
obj.ToMap<T>();

/// Extension method to map the data reader with list.
DbDataReader.MapToList<T>();

/// Extension method to map the database table with list.
DataTable.MapToList<T>();

```
**Date:**
```
/// Extension method to returns the first day of the month.
DateTime.FirstDayOfMonth();

/// Extension method to returns the last day of month.
DateTime.LastdayOfMonth();

/// Extension method returns the first day of the week.
DateTime.FirstDayOfWeek();

/// Extension method returns the last day of the week.
DateTime.LastDayOfWeek();

/// Extension method returns the first day of next month.
DateTime.FirstDayOfNextMonth();

> How to get last date of next month?
DateTime.FirstDayOfNextMonth().LastdayOfMonth();

```
**Enum:**
```
/// Extension method to convert the string into generic enum.
string.ToEnum<T>();

/// Extension method to convert the enum value into non pascal string.
enum.ToPascalWordSeparatedString();
```
**String:**
```
/// Extension method shuffle the characters of string.
String.Shuffle();

/// Extension method to extract only numbers from string.
String.ExtractDigits();

/// Extension method to extract only Characters(A-Z/a-z) from string. 
String.ExtractAlphabets();

/// Extension method to encrypt the string.
String.Encrypt(string passPhrase, string initVector);

/// Extension method to decrypt the encrypted string.
String.Decrypt(string passPhrase, string initVector);
```

**3. AT.NetCore.Common.Cryptography**

This class provides the functionality to encrypt/decrypt the text. This is specially using for Password. Behind the scene, **AT.NetCore.Encipher.Bluefish** library is used.

**Text**
This class provides the functionality to encrypt/decrypt the text.

**Properties:**
```
/// <summary>
/// Sets the encryption/decryption passpharse.
/// </summary>
public static string PassPharase { sets; }

/// <summary>
/// Sets the encryption/decryption init vector value.
/// <para>It must contain 16 characters. </para>
/// </summary>
/// <example>@#ATExamplesk5@@</example>
public static string InitVector { sets; }

/// <summary>
/// Method to encrypt the given string.
/// </summary>
/// <param name="IsRecoverable">Provide bool value to set the plainString will be recoverable or not.</param>
/// <param name="plainString">String that to be encrypted.</param>
/// <returns></returns>
public static string Encrypt(bool IsRecoverable, string plainString)

/// <summary>
/// Generic method to decrypt the string.
/// </summary>
/// <param name="encryptedString">Encrypted string to decrypt.</param>
/// <returns></returns>
public static T Decrypt<T>(string encryptedString)
/// <summary>
/// Method to decrypt the encrypted string.
/// </summary>
/// <param name="encryptedString"></param>
/// <returns></returns>
public static string Decrypt(string encryptedString)
```

**File**
This class provides the functionality to encrypt/decrypt the text file.

**Properties:**

These are the two properties to set the public and private keys for encryption and decryption.
```
/// <summary>
/// Sets the encryption/decryption key. It must be 8 bit.
/// </summary>
public static string Key { sets; }

/// <summary>
/// Sets the encryption initialization vector value.
/// </summary>
public static string InitializationVector { sets; }
```
**Methods:**
```
/// <summary>
/// Method to encrypt the file.
/// </summary>
/// <param name="filePath">Provide file location path.</param>
/// <param name="filename">Provide filename into the data will be saved in encrypted form.</param>
/// <param name="data">Provide the text data object.</param>
/// <exception cref="ArgumentNullException"></exception>
public static void EncryptAndCreateOrUpdateFile<T>(string filePath, string filename, T data)

/// <summary>
/// Generic method to decrypt the file.
/// </summary>
/// <typeparam name="T">Generic type</typeparam>
/// <param name="fileLocation">Provide the file which has to be decrypted.</param>
/// <returns></returns>
public static T Decrypt<T>(string fileLocation)
```
  
**4. AT.NetCore.Common.Serialization**
  
This class provide the JSON serialization and deserialization functionality.

**JSON**
```
/// <summary>
/// Generic method to serialize the object.
/// </summary>
/// <typeparam name="T">Provide type of object.</typeparam>
/// <param name="objData">Provide object that to be serialized.</param>
/// <returns></returns>
public static string Serialize<T>(T objData)
/// <summary>
/// Generic method to deserialize into the object.
/// </summary>
/// <typeparam name="T">Provide type of object.</typeparam>
/// <param name="data">Provide JSON string to be deserialized.</param>
/// <returns></returns>
public static T DeSerialize<T>(string data)
```
**XML**
```
/// <summary>
/// Static method to serialize the object.
/// </summary>
/// <param name="data">Provide the object of data that needs to be serialize in XML.</typeparam>
/// <param name="filename">Provide the filename into which the xml will be written.</param>
/// <param name="preFix">Provide any xml prefix.</param>
/// <param name="nameSpace">Provide namespace</param>
void Serialize<T>(object data, string filename, string preFix, string nameSpace= "http://www.sitemaps.org/schemas/sitemap/0.9")
					  
/// <summary>
/// Static Method to de-serialize into the object.
/// </summary>
/// <typeparam name="T">Provide type of object.</typeparam>
/// <param name="filename">Provide XML filename</param>
/// <returns></returns>
T DeSerialize<T>(string filename)

/// <summary>
/// Static method to de-serialize the memory stream xml data.
/// </summary>
/// <typeparam name="T"></typeparam>
/// <param name="memoryStream"></param>
/// <returns></returns>
static T DeSerialize<T>(MemoryStream memoryStream)
```
