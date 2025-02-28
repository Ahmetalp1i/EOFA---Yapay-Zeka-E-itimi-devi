import requests

api_key = "28415653ad5e4bf3b3c05beecd8d33bd"
url = "https://newsapi.org/v2/top-headlines"
params = {'country': 'us', 'apiKey': api_key}
res = requests.get(url, params=params)
if res.ok:
    haberler = res.json().get('articles', [])
    if haberler:
        for h in haberler:
            print(f" {h.get('title', 'Başlık yok')}\n {h.get('publishedAt', 'Tarih yok')}\n"
                  f" {h.get('url', 'Link yok')}\n{'-' * 50}")
    else:
        print("Hiç haber bulunamadı.")
else:
    print(f" Hata {res.status_code}: {res.text}")
