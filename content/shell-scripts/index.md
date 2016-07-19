# Shell Script

* [Download and Execute a Script from Remote](#download-and-excute-a-script-from-remote)
* [CURL Example Usage]()
* [References](#references)


#### Download and Execute a Script from Remote

option1
```
curl https://gist.githubusercontent.com/bobwei/19d3cd97a99953c0b572cf50b83c2dd6/raw/98ec7a4ee9467ed620e2b50580a667620f73597f/test.sh | sh
```

option2
```
bash -c "$(curl https://gist.githubusercontent.com/bobwei/19d3cd97a99953c0b572cf50b83c2dd6/raw/98ec7a4ee9467ed620e2b50580a667620f73597f/test.sh)"
```

[ruby sample](http://brew.sh/)
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Notes :

* [curl option explaned](http://explainshell.com/explain?cmd=curl+-fsSL+example.org)


#### CURL Example Usage

POST data with headers
```
curl -X POST \
  -H "X-Parse-Application-Id: Zq62OnlXqwL3Yq47v1L3sH5ZxMnEPO8Evik49P4p" \
  -H "X-Parse-REST-API-Key: EDhO5qljdikm0DbVH5IpvEKzl4LmGO6QrTlCGyUV" \
  -H "Content-Type: application/json" \
  -d '{"score":1337,"playerName":"Sean Plott","cheatMode":false}' \
  https://api.parse.com/1/classes/GameScore
```


#### References

* [node and npm in 30 seconds](https://gist.github.com/isaacs/579814)
