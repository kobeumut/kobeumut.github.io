---
title: Swift En Basit Veri Çekme ve Parse İşlemi
layout: post
date: '2018-01-07 21:00:00'
categories: Swift
---

## En Basit Haliyle Veri Çekip JSON Parse İşlemi [Swift 4]

Swift 4 ile gelen codable kütüphanesi ile artık decode ve encode işlemlerini tek bir model ile halledebiliyoruz.

Burada yapmamız gereken struck cinsi ile hazırladığımız modeli codable'dan extend etmek. Şöyleki githubdan veri çektiğimizi varsayıp şöyle bir model oluşturalım ve URLSession ile verileri çekip print ile consola yazdıralım. Bunu da bir fonksiyon içerisine koyup o şekilde çağıralım.

Şimdi fetchResultsFromApi() adlı fonksiyonumuzu istediğimiz yerde çalıştırıp console'da gelen veriyi görebiliriz.

```swift
func fetchResultsFromApi() {
        struct MyGitHub: Codable {
            
            let name: String?
            let location: String?
            let followers: Int?
            let avatarUrl: URL?
            let repos: Int?
            
            private enum CodingKeys: String, CodingKey {
                case name
                case location
                case followers
                case repos = "public_repos"
                case avatarUrl = "avatar_url"
                
            }
        }
        guard let gitUrl = URL(string: "https://api.github.com/users/kobeumut") else { return }
        URLSession.shared.dataTask(with: gitUrl) { (data, response
            , error) in
            guard let data = data else { return }
            do {
                let decoder = JSONDecoder()
                let gitData = try decoder.decode(MyGitHub.self, from: data)
                print(gitData.name ?? "Empty Name")
                
            } catch let err {
                print("Err", err)
            }
            }.resume()
    }
```