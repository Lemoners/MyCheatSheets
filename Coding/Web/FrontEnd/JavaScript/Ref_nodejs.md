# Node.js ѧϰ�ʼ�

## ģ�黯

Node ���� JavaScript �ĺ���ʽ������ԣ�ʵ��ģ��ĸ��롣

```javascript
(function() { ... })();
```

ʹ�� `module.exports = <functionName>` ��������¶��ȥ�� ���ô��� `require('<module_name>')` �õ���¶�ĺ�����

## ����ģ��

### fs

�ļ�ϵͳģ�� `fs`: ��Ϊ**�첽����**��***ͬ������**��

- �첽���ļ�: `fs.readFile('<FileName>', 'utf-8', function(err, data){ ... });`
- ͬ�����ļ�: `var data = fs.readFileSync('<FileName>', 'utf-8');`
    ����ͨ�� `try {...} catch() {...}` ����
- �첽д�ļ�: `fs.writeFile('<FileName>', data, function(err) { ... });`
    ����� data �� String, Ĭ�ϰ� UTF-8 д�룬����� data �� Buffer, ��д��������ļ���
- ͬ��д�ļ�: `fs.writeFileSync('<FileName>', data);`
- �첽��ȡ�ļ�����: `fs.stat('<FileName>', function(err, stat) { ... });`
- ͬ����ȡ�ļ�����: `var stat = fs.statSync('<FileName>');`

### stream

��������ȡ/д�� `fs.createReadStream`, `fs.createWriteStream`

�ܵ����� `readable.pipe(writeable, {end:true/false});`

### http

- `http` ģ�� - �ṩ `request` �� `response` ����
    `http.createServer(function(request, response) {...});` ���� Web Server
- `url` ģ�� - web ·��
- `path` ģ�� - �����ļ�Ŀ¼

### crypto

`crypto` �ṩ ���ܺ͹�ϣ�㷨��

- `crypto.createHash('md5');` - ��ϣ�㷨 MD5��SHA1
- `crypto.createHmac('sha256', 'secret-key');` - ��ϣ�㷨 Hmac ��Ҫ�����һ����Կ
- `crypto.createCipher('aes192', 'secret-key');` - AES �ԳƼ����㷨, �ӽ�����ͬһ����Կ
- `crypto.createDiffieHellman(prime, generator);` - DH �㷨����Կ����Э�飬˫���ڲ�й¶��Կ�����������һ����Կ
- `crypto.create` - �ǶԳ��㷨��RSA һ����Կ��һ��˽Կ������Կ��
    RSA ���ʺϼ��ܴ����ݣ����ڴ����ݼ��ܣ�������һ�� AES ��Կ���ܴ����ݣ�Ȼ���� RSA ���� AES ��Կ��ʵ��ʹ��ʱ������ AES �� RSA 2 ����Կ��

## Web ����

### koa
