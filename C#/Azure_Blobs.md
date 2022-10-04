## Writing object as csv to blob

The instance of the blobclient is created outside of this method.

```
// Using a stream for this. There are ways to write a string f.eks, but not for now.
// Using a memorystream, storing it in RAM and discarding after use.
using (var memoryStream = new MemoryStream())
{
  // Creating a writer for the stream
  using (var streamWriter = new StreamWriter(memoryStream))
  // CsvHelper has a wrapper for a writer to write CSV to the stream.
  using (var csvWriter = new CsvWriter(streamWriter, CultureInfo.InvariantCulture))
  {
    // Use csvWriter to write the list to the stream
    csvWriter.WriteRecords(userInputReport);
    // Force the underlying writer to complete the write
    streamWriter.Flush();
    // Reset the stream to index 0 before upload, forgetting this will make an empty file
    memoryStream.Seek(0, SeekOrigin.Begin);
    // Upload the stream to the blob in Azure.
    await _targetBlobClient.UploadAsync(memoryStream);
                    
  }
}
```
