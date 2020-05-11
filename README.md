# Selecionar apenas mês e ano

- Referência [react-native-month-selector](https://github.com/vinodkumar8/react-native-month-selector)

- Instalar dependência:

```bash
yarn add react-native-month-selector
```

- Instalar a dependencia `moment`:

```bash
yarn add moment
```

- Talvez não seja necessário mas eu sempre faço: abrir a pasta `ios/` e executar o comando:

```bash
pod install
```

- Criar o arquvio `src/App.js`:

```js
import React, {useState, useEffect} from 'react';
import {View, Text} from 'react-native';
import moment from 'moment';
import {pt} from 'moment/locale/pt-br';
import MonthSelectorCalendar from 'react-native-month-selector';

moment.locale(pt);

export default function MyDatePicker() {
  const [month, setMonth] = useState(null);

  useEffect(() => {
    setMonth(moment('29/08/2019', 'DD/MM/YYYY', true));
  }, []);

  return (
    month && (
      <View style={{flex: 1, alignItems: 'center', justifyContent: 'center'}}>
        <Text>
          Selected Month is {month && moment(month).format('MMMM/YYYY')}
          {/* this.state.month && this.state.month.format('MMM YYYY') */}
        </Text>
        <MonthSelectorCalendar
          localeLanguage="pt-br"
          nextText="Próx"
          prevText="Ant"
          /*
        initialView={moment('29/07/2018', 'DD/MM/YYYY')}
        currentDate={moment('29/07/2018', 'DD/MM/YYYY')}
        selectedDate={moment('29/07/2018', 'DD/MM/YYYY', true)}
        */
          initialView={moment(month)}
          currentDate={moment(month)}
          selectedDate={moment(month)}
          onMonthTapped={date => setMonth(date)}
        />
      </View>
    )
  );
}

```

- No arquivo `./index.js` alterar:

```js
import App from './src/App';
```