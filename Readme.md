# react-native-card-swip

[![NPM version](https://badge.fury.io/js/react-native-backgroud-shapes.svg)](https://npmjs.org/package/react-native-backgroud-shapes) [![GitHub license](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](https://raw.githubusercontent.com/kevoj/react-native-backgroud-shapes/master/LICENSE)

> Beautiful Card Swiper to React Native 

### Examples

<p align="center">
<img  src="https://res.cloudinary.com/kush636/image/upload/v1581577154/swip.gif" width="400" >
</p>

### Installation

**Yarn**

```bash
yarn add react-native-card-swip
```

**Npm**

```bash
npm i  react-native-card-swip
```

### Usage

```javascript
import React, {PureComponent} from 'react';
import {View, Text, StyleSheet} from 'react-native';
import {Card, Button} from 'react-native-elements';
import CardSwiper from 'react-native-card-swip';

class App extends PureComponent {
  constructor(props) {
    super(props);
    this.state = {
      serverData: [],
    };
    fetch(
      'https://newsapi.org/v2/top-headlines?country=in&apiKey=e9ed76ff6496462b8096d1e4b3178434',
      {
        method: 'GET',
      },
    )
      .then(response => response.json())
      .then(responseJson => this.setState({serverData: responseJson.articles}))
      .catch(err => {
        alert(err, 'Sorry for error');
      });
  }

  renderCard(item) {
    return (
      <View style={{alignSelf: 'center'}}>
        <Card key={item.title} image={{uri: item.urlToImage}}>
          <Text style={{marginBottom: 10, height: 50, width: null}}>
            {item.description}
          </Text>
        </Card>
      </View>
    );
  }

  renderNoMoreCards() {
    return (
      <Card title="All done">
        <Text>There is no more content</Text>
        <Button title="Get More" />
      </Card>
    );
  }

  render() {
    return (
      <View style={styles.container}>
        <CardSwiper
          data={this.state.serverData}
          renderCard={this.renderCard}
          onSwipeLeft={item => console.log(item, 'onSwipeLeft')}
          onSwipeRight={item => console.log(item, 'onSwipeRight')}
          renderNoMoreCards={this.renderNoMoreCards}
        />
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
  },
});
export default App;

```

### Options/Props

```javascript

<CardSwiper
          data={this.state.serverData}
          renderCard={this.renderCard}
          onSwipeLeft={item => console.log(item, 'onSwipeLeft')}
          onSwipeRight={item => console.log(item, 'onSwipeRight')}
          renderNoMoreCards={this.renderNoMoreCards}
/>


## License

MIT © [Kush Kumar](https://github.com/kush11/react-native-card-swip)