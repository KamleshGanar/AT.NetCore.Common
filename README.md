# AT.NetCore.Common
In the programming world the developers must have to note some common functions/methods into somewhere in mind or maintain notebook. 
This AT.NetCore.Common library provides those kind of common functions/methods and it reduces 30% developers coding time. I am not saying that AT.NetCore.Common libary has provided very extensive methods. In fact, the small methods that are regularly useful in our day-to-day coding.

###### AT.NetCore.Common has following namespaces underwhich static classes are defined.
```
1. AT.NetCore.Common
	└ PubliceProcedures
2. AT.NetCore.Common.Convert
	├ Data
	└ Timezone
3. AT.NetCore.Common.Encipher
	├ Text
	└ File
4. AT.NetCore.Common.Serialization
	└ JSON
```

## In Detail

**1. AT.NetCore.Common.PublicProcedures**

This class contains the useful properties and method to serve the helpful functionality to enhance and reduce the coding efforts. 

**Method:**
```
	/// <summary>
	/// Method to convert the currency into words.
	/// </summary>
	/// <param name="number">Provide amount</param>
	/// <param name="currency">Provide currency name</param>
	/// <param name="monetaryUnit">Provide monetary unity name</param>
	/// <exception cref="ArgumentEmptyException"></exception>
	/// <exception cref="InvaildNumberStringException"></exception>
	/// <returns></returns>
	public static String ConvertCurrencyToWords(String number, string currency = "Rupees", string monetaryUnit = "Paisa")

	/// <summary>
	/// Method to convert number into words.
	/// </summary>
	/// <param name="number">Provide number.</param>
	/// <returns></returns>
	/// <exception cref="ArgumentEmptyException"></exception>
	public static String ConvertNumberToWords(String number)

  /// <summary>
  /// Static method to get the permutation numbers of sum check value.
  ///<para>sumCheckValue is the addition of any combination of 2^n. Here n is 1,2,3,4,5,6,.....n </para>
  /// </summary>
  /// <param name="sumCheckValue">Provide the sum check value.</param>
  /// <returns></returns>
  public static List<long> GetPermutation(long sumCheckValue)
		
  /// <summary>
  /// Method to get the public/external IP address.
  /// <param name="errorMessage">Provide error message holding parameter.</param>
  /// </summary>
  /// <returns></returns>
  public static string GetIPAddress(ref string errorMessage)
		
  /// <summary>
  /// Extension method to convert the enum value into non pascal string.
  /// </summary>
  /// <param name="enu">Provide enum value</param>
  /// <returns></returns>
  public static string EnumValueToNonPascalString(this Enum enu)
		
  /// <summary>
  /// Method to read the excel file and return data in table form.
  /// </summary>
  /// <param name="path">Provide the excel sheet file.</param> 
  /// <param name="sheetName">Provide the sheetname</param>
  /// <param name="hasHeader">Provide the boolean value to check the sheet has first row as header or not.</param>
  /// <returns></returns>
  /// <exception cref="FilePathEmptyException"></exception>
  /// <exception cref="FileNotFoundException"></exception>
  /// <exception cref="SheetnameEmptyException"></exception>
  public static DataTable ReadExcelToTable(string path, string sheetName, bool hasHeader = true)
		
  /// <summary>
  /// This method generates the GUID string.
  /// </summary>
  /// <returns></returns>
  public static string GenerateGUID(GUIDExtraction extraction = GUIDExtraction.AlphaNumbers, int? length = 10)
		
  /// <summary>
  /// Static method to extract only numbers from Value string.
  /// </summary>
  /// <param name="value">String from which digits will be extracted</param>
  /// <returns></returns>
  public static string ExtractDigits(string value)
		
  /// <summary>
  /// Static method to extract only Characters(non-digit) from Value string. 
  /// </summary>
  /// <param name="value">String from which alphabets will be extracted</param>
  /// <returns></returns>
  public static string ExtractCharacter(string value)
		
  /// <summary>
  /// Method returns the list of timezones.
  /// </summary>
  /// <returns></returns>
  public static ReadOnlyCollection<TimeZoneInfo> GetTimezones()
		
  /// <summary>
  /// Method returns the list of timezones async.
  /// </summary>
  /// <returns></returns>
  public static async Task<ReadOnlyCollection<TimeZoneInfo>> GetTimezonesAsync()
		
  /// <summary>
  /// Static method to get relative folder to create the sub folders.
  /// <para>If the sub folder is not present then will create it according to Year/Month</para>
  /// </summary>
  /// <param name="defaultFolder">Provide default folder</param>
  /// <example>~/2017/March/Documents. Here /Documents is a default folder.</example>
  /// <param name="errorMessage">Provide error message holding parameter.</param>
  /// <param name="subFoldersInDefaultFolder">Provide the sub folder path in side the default folder.</param>
  /// <returns></returns>
  public static string CreateFolder(string defaultFolder, ref string errorMessage, string subFoldersInDefaultFolder = null)
		
  /// <summary>
  /// Method to check the credit card number is valid or invalid.
  /// </summary>
  /// <param name="cardNumber"></param>
  /// <returns></returns>
  public static bool IsValidCreditCard(string cardNumber)
```

**2.1 AT.NetCore.Common.Convert.Data**

This class provides the functionality for data conversion.

**Methods:**
```
  /// <summary>
  /// Method to convert the generic object into bytes.
  /// </summary>
  /// <typeparam name="T"></typeparam>
  /// <param name="obj"></param>
  /// <returns></returns>
  public static byte[] ToBytes<T>(T obj)
		
  /// <summary>
  /// Method to convert the data bytes into the generic object.
  /// </summary>
  /// <typeparam name="T"></typeparam>
  /// <param name="data"></param>
  /// <returns></returns>
  public static T ToObject<T>(byte[] data)
		
  /// <summary>
  /// Generic Static method to create the clone of object.
  /// </summary>
  /// <typeparam name="T">Provide the object type.</typeparam>
  /// <param name="t">Provide the object type</param>
  /// <returns></returns>
  public static T CreateClone<T>(T t)
```

**2.2 AT.NetCore.Common.Convert.Timezone**

The class provides the functionality for timezone date conversion

**Methods:**
```
  /// <summary>
  /// Static method to convert the datetime into UTC datetime.
  /// </summary>
  /// <param name="value">Convertible datetime</param>
  /// <param name="timeZone">Timezone name</param>
  /// <returns></returns>
  public static DateTime? ConvertToUTC(DateTime value, string timeZone = null)
		
  /// <summary>
  /// Static metod to convert the UTC datetime into system datetime.
  /// </summary>
  /// <param name="value">Convertible datetime</param>
  /// <param name="timeZone">Timezone name</param>
  /// <returns></returns>
  public static DateTime? ConvertFromUTC(DateTime value, string timeZone = null)
```

**3.1. AT.NetCore.Common.Encipher.Text**

This class provides the functionality to encrypt/decrypt the text. This is specially using for Password. Behind the scene, **MD5 and Rijndael algorithm** are used.

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
```

**Methods:**
```
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

**3.2. AT.NetCore.Common.Encipher.File**

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
  
**4.1. AT.NetCore.Common.Serialization.JSON**
  
This class provide the JSON serialization and deserialization functionality.

**Method:**
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

**NOTE :** This library fetch user's public IP for statistics and analysis purpose.
