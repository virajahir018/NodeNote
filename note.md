# CJS AND ESM :
  CJS और ESM जावास्क्रिप्ट में कोड को व्यवस्थित और शेयर (import/export) करने के दो अलग-अलग तरीके (मॉड्यूल सिस्टम) हैं।

  # CJS (CommonJS) क्या है?
    यह Node.js का पुराना और पारंपरिक मॉड्यूल सिस्टम है।इसमें कोड को लोड करने के लिए require() और बाहर भेजने के लिए module.exports का इस्तेमाल होता है।यह सिंक्रोनस (Synchronous) तरीके से काम करता है, यानी फाइलें एक-एक करके लाइन से लोड होती हैं। यह सर्वर-साइड (Backend) के लिए ठीक है, लेकिन ब्राउज़र के लिए धीमा हो सकता है।

  # ESM (ECMAScript Modules) क्या है?
    यह जावास्क्रिप्ट का नया और आधिकारिक (Official) मानक तरीका है।इसमें कोड को जोड़ने के लिए import और बाहर भेजने के लिए export कीवर्ड का उपयोग होता है।यह एसिंक्रोनस (Asynchronous) तरीके से काम करता है, जिससे ब्राउज़र और आधुनिक रनटाइम में फाइलें तेजी से लोड होती हैं। इसमें 'ट्री-शेकेबिलिटी' (Tree-shaking) की सुविधा भी मिलती है, यानी जो कोड काम का नहीं है वह हट जाता है।

# Module kya hai ?
  Module ka matlab hota hai JavaScript code ko alag-alag files me divide karna, taaki code clean, reusable aur maintainable rahe.

# Tree Shaking?
  Tree Shaking ek optimization technique hai jo unused code ko final bundle se hata deti hai.

  Unused code ko remove karke sirf zaroori code ko final bundle me rakhna.

  # Tree Shaking ka fayda :
     Bundle size chhota hota hai.
     Website jaldi load hoti hai.
     Kam data download hota hai.
     Better performance milti hai.