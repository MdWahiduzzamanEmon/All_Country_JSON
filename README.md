# All Country JSON Data 🌍

A comprehensive JSON dataset containing information for 242 countries, including country names, dial codes, and ISO country codes.

## 📋 Data Structure

Each country entry contains:
- `name`: Country name (string)
- `dial_code`: International dialing code (string)
- `code`: ISO 3166-1 alpha-2 country code (string)

## 📦 Installation & Usage

### NPM Installation

> **Note**: The package is ready for NPM but not yet published. See [PUBLISHING.md](PUBLISHING.md) for publishing instructions.

Once published, you can install via NPM:
```bash
npm install all-country-json
```

Then in your code:
```javascript
const countries = require('all-country-json');
console.log(countries.length); // 242
```

### Direct Download

Download the `All_Country.json` file directly from this repository.

### Via CDN (jsDelivr)

```
https://cdn.jsdelivr.net/gh/MdWahiduzzamanEmon/All_Country_JSON@main/All_Country.json
```

### Via Raw GitHub URL

```
https://raw.githubusercontent.com/MdWahiduzzamanEmon/All_Country_JSON/main/All_Country.json
```

## 💻 Code Examples

### JavaScript (Browser)

```javascript
// Fetch the data
fetch('https://cdn.jsdelivr.net/gh/MdWahiduzzamanEmon/All_Country_JSON@main/All_Country.json')
  .then(response => response.json())
  .then(countries => {
    console.log(countries);
    // Find a specific country
    const usa = countries.find(country => country.code === 'US');
    console.log(usa); // { name: "United States", dial_code: "+1", code: "US" }
  });
```

### JavaScript (Node.js)

```javascript
const fs = require('fs');

// Read local file
const countries = JSON.parse(fs.readFileSync('./All_Country.json', 'utf8'));

// Find country by name
const country = countries.find(c => c.name === 'Bangladesh');
console.log(country);

// Get all countries with specific dial code
const usDial = countries.filter(c => c.dial_code === '+1');
console.log(usDial);
```

### Python

```python
import json
import requests

# From URL
response = requests.get('https://cdn.jsdelivr.net/gh/MdWahiduzzamanEmon/All_Country_JSON@main/All_Country.json')
countries = response.json()

# Find a country
usa = next((c for c in countries if c['code'] == 'US'), None)
print(usa)

# Or read from local file
with open('All_Country.json', 'r') as f:
    countries = json.load(f)
    print(f"Total countries: {len(countries)}")
```

### PHP

```php
<?php
// From URL
$json = file_get_contents('https://cdn.jsdelivr.net/gh/MdWahiduzzamanEmon/All_Country_JSON@main/All_Country.json');
$countries = json_decode($json, true);

// Find a country
foreach ($countries as $country) {
    if ($country['code'] === 'BD') {
        print_r($country);
        break;
    }
}
?>
```

## 🔍 Common Use Cases

### Search/Filter Examples

#### Find country by code

```javascript
const getCountryByCode = (countries, code) => {
  return countries.find(country => country.code === code);
};

const japan = getCountryByCode(countries, 'JP');
```

#### Find country by dial code

```javascript
const getCountryByDialCode = (countries, dialCode) => {
  return countries.filter(country => country.dial_code === dialCode);
};

const ukCountries = getCountryByDialCode(countries, '+44');
```

#### Search country by name

```javascript
const searchCountryByName = (countries, searchTerm) => {
  return countries.filter(country => 
    country.name.toLowerCase().includes(searchTerm.toLowerCase())
  );
};

const results = searchCountryByName(countries, 'united');
```

#### Get all unique dial codes

```javascript
const uniqueDialCodes = [...new Set(countries.map(c => c.dial_code))];
```

#### Sort countries alphabetically

```javascript
const sortedCountries = [...countries].sort((a, b) => 
  a.name.localeCompare(b.name)
);
```

## 🎯 Use Cases

This dataset is perfect for:
- Country selection dropdowns in web forms
- Phone number input with country code selection
- Country-based filtering and search functionality
- Geographic data visualization
- International applications requiring country data
- Educational projects and data analysis

## 📊 Data Sample

```json
[
  {
    "name": "Afghanistan",
    "dial_code": "+93",
    "code": "AF"
  },
  {
    "name": "Albania",
    "dial_code": "+355",
    "code": "AL"
  },
  {
    "name": "United States",
    "dial_code": "+1",
    "code": "US"
  }
]
```

## 📈 Statistics

- Total Countries: **242**
- Data Format: **JSON**
- File Size: **~18 KB**

## 📤 Publishing to NPM

**For Maintainers**: This package is ready to publish to NPM!

- **Quick Start**: See [QUICKSTART.md](QUICKSTART.md) for a simple guide to publish for the first time
- **Detailed Guide**: See [PUBLISHING.md](PUBLISHING.md) for comprehensive instructions including:
  - Setting up NPM credentials
  - Manual publishing steps
  - Automated publishing with GitHub Actions
  - Version management
  - Best practices

## 🤝 Contributing

Contributions are welcome! If you find any errors or want to add more data fields, please:
1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## 📝 License

MIT License - see [LICENSE](LICENSE) file for details.

## 🔗 Related Projects

If you need more detailed country information, consider:
- [REST Countries API](https://restcountries.com/)
- [Country List](https://github.com/umpirsky/country-list)
- [World Countries](https://github.com/mledoze/countries)

## ⭐ Support

If you find this useful, please give it a star ⭐ and share it with others!

---

**Maintained by**: [MdWahiduzzamanEmon](https://github.com/MdWahiduzzamanEmon)