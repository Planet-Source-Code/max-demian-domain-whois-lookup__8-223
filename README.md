<div align="center">

## Domain Whois Lookup


</div>

### Description

do a domain whois lookup from your own site, just input the whois server & website (no www.)
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Max Demian](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/max-demian.md)
**Level**          |Advanced
**User Rating**    |5.0 (15 globes from 3 users)
**Compatibility**  |PHP 3\.0, PHP 4\.0
**Category**       |[Internet/ Browsers/ HTML](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/internet-browsers-html__8-9.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/max-demian-domain-whois-lookup__8-223/archive/master.zip)





### Source Code

```
<?
// Domain Whois Lookup
// Writer: Max - Demian Net
// E-Mail: Max@Wackowoh.com
// WebSite: http://www.DemianNet.com http://www.Wackowoh.com
// Language: PHP
function whois_request($server, $query) {
  $data = "";
  $fp = fsockopen($server, 43);
  if($fp) {
   fputs($fp, $query."\r\n");
   while(!feof($fp)) {
     $data .= fread($fp, 1000);
   }
   fclose($fp);
  }
  return $data;
}
?>
<FORM>
  <INPUT TYPE=HIDDEN NAME=action VALUE=query>
  Server: <INPUT TYPE=TEXT NAME=server VALUE="<?echo $server?>"> <SMALL>(ie: whois.networksolutions.com)</SMALL><BR>
  Domain: <INPUT TYPE=TEXT NAME=query VALUE="<?echo $query?>"> <SMALL>(ie: wackowoh.com)</SMALL><BR>
  <INPUT TYPE=SUBMIT VALUE=" OK ">
</FORM>
<?
if($action == "query") {
  $data = whois_request($server, $query);
  echo "Sent $query to $server.<p>";
  echo "Output: <p><pre>$data</pre><p>";
}
?>
```

