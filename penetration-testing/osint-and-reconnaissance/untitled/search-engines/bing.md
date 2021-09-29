# Bing

Microsoft provide a search engine in the form of [Bing](https://www.bing.com/). Whilst it is not as popular as Google, Bing is still a powerful engine and can turn some interesting results out. Much like the others, Bing also supports operators:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Keyword</th>
      <th style="text-align:left">Definition</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>contains:</code>
      </td>
      <td style="text-align:left">Keeps results focused on sites that have links to the file types that
        you specify.</td>
      <td style="text-align:left">To search for websites that contain links to Windows Media Audio (.wma)
        files, type music contains:wma.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>ext:</code>
      </td>
      <td style="text-align:left">Returns only webpages with the filename extension that you specify.</td>
      <td
      style="text-align:left">To find reports created only in DOCX format, type your subject, followed
        by ext:docx.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>filetype:</code>
      </td>
      <td style="text-align:left">Returns only webpages created in the file type that you specify.</td>
      <td
      style="text-align:left">To find reports created in PDF format, type your subject, followed by
        filetype:pdf.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>inanchor:</code>
        </p>
        <p><code>or</code>
        </p>
        <p><code>inbody:</code>
        </p>
        <p><code>or</code>
        </p>
        <p><code>intitle:</code>
        </p>
      </td>
      <td style="text-align:left">These keywords return webpages that contain the specified term in the
        metadata, such as the anchor, body, or title of the site, respectively.
        Specify only one term per keyword. You can string multiple keyword entries
        as needed.</td>
      <td style="text-align:left">To find webpages that contain &#x201C;msn&#x201D; in the anchor, and the
        terms &#x201C;spaces&#x201D; and &#x201C;magog&#x201D; in the body, type
        inanchor:msn inbody:spaces inbody:magog.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>ip:</code>
      </td>
      <td style="text-align:left">Finds sites that are hosted by a specific IP address. The IP address must
        be a dotted quad address. Type the ip: keyword, followed by the IP address
        of the website.</td>
      <td style="text-align:left">Type IP:207.46.249.252.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>language:</code>
      </td>
      <td style="text-align:left">Returns webpages for a specific language. Specify the language code directly
        after the language: keyword.</td>
      <td style="text-align:left">To see webpages only in English about antiques, type &quot;antiques&quot;
        language:en.</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><code>loc:</code>
        </p>
        <p><code>or</code>
        </p>
        <p><code>location:</code>
        </p>
      </td>
      <td style="text-align:left">Returns webpages from a specific country or region. Specify the country
        or region code directly after the loc: keyword. To focus on two or more
        languages, use a logical OR to group the languages.</td>
      <td style="text-align:left">To see webpages about sculpture from the U.S. or Great Britain, type sculpture
        (loc:US OR loc:GB). For a list of language codes that you can use with
        Bing, see Country, region, and language codes.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>prefer:</code>
      </td>
      <td style="text-align:left">Adds emphasis to a search term or another operator to help focus the search
        results.</td>
      <td style="text-align:left">To find results about football but that primarily pertain to the organization,
        type football prefer:organization.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>site:</code>
      </td>
      <td style="text-align:left">Returns webpages that belong to the specified site. To focus on two or
        more domains, use a logical OR to group the domains. You can use site:
        to search for web domains, top level domains, and directories that are
        not more than two levels deep. You can also search for webpages that contain
        a specific search word on a site.</td>
      <td style="text-align:left">To see webpages about heart disease from the BBC or CNN websites, type
        &quot;heart disease&quot; (site:bbc.co.uk OR site:cnn.com). To find webpages
        about the PC version of Halo on the Microsoft website, type site:www.microsoft.com/games/pc
        halo.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>feed:</code>
      </td>
      <td style="text-align:left">Finds RSS or Atom feeds on a website for the terms you search for.</td>
      <td
      style="text-align:left">To find RSS or Atom feeds about football, type feed:football.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>hasfeed:</code>
      </td>
      <td style="text-align:left">Finds webpages that contain an RSS or Atom feed on a website for the terms
        you search for.</td>
      <td style="text-align:left">To find webpages on the New York Times website that contain RSS or Atom
        feeds, type site:www.nytimes.com hasfeed:football.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>url:</code>
      </td>
      <td style="text-align:left">Checks whether the listed domain or web address is in the Bing index.</td>
      <td
      style="text-align:left">To verify that the Microsoft domain is in the index, type url:microsoft.com.</td>
    </tr>
  </tbody>
</table>



