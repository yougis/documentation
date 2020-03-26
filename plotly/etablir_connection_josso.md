
# Traiter des données json depuis une api Rest
## Avec pandas

Etablir une connexion sécurisée avec les api PSUD (josso)

```python
import urllib , requests, base64
dev = 'true'
baseUrlDev = 'http://localhost'
baseUrl = 'https://psud.nc'
login = "hugo.roussaffa"
login = login + '@province-sud.nc'
password = "MCOT9A9.u"
loginDev = "a"
passwordDev = ""
jossoEndpointDev = '/j_security_check'

cookies={}

headers = {}
headers['User-Agent'] = 'plotly'
headers['Content-Type'] = 'application/json'


if dev=='true' :
  login = loginDev
  password = passwordDev
  baseUrl = baseUrlDev
  post_url = baseUrl
  post_data = urllib.parse.urlencode({
  'j_username':login,
  'j_password':password,
  }).encode('ascii')
  concatenated = login + ":" + password
  data = base64.b64encode(concatenated.encode('ascii'))
  headerData = "Basic " + data.decode('ascii')
  headers["Authorization"] = headerData.encode('ascii')

else:
  post_url = baseUrl + jossoEndpoint
  post_data = urllib.parse.urlencode({
  'josso_username':login,
  'josso_password':password,
  'josso_cmd':'login'
  }).encode('ascii')
  post_response = urllib.request.urlopen(url=post_url, data=post_data)

  #on récupère le cookie JOSSO_SESSION_ID
  jsessionId = post_response.getheader('Set-Cookie').split(',')[0].split(';')[0].strip()
  josso_sessionId = post_response.getheader('Set-Cookie').split(',')[1].split(';')[0].strip()

  cookies.update([(josso_sessionId.split('=')[0],josso_sessionId.split('=')[1])])
  cookies.update([(jsessionId.split('=')[0],jsessionId.split('=')[1])])
  cookies.update([('usernameLoginJOSSO',login)])

req = requests.get(baseUrl+'/odk/odk/ElementGeometry/ff80818171044e3a01710455f0260064?_responseMode=json',cookies=cookies, headers=headers)
req.text
