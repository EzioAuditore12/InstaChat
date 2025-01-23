# Setting Up this Project

## Package used for navigation

1. For Icons in UI, we are using React-native-vector-icons

    1. Install The package
    ```bash
    npm install --save react-native-vector-icons
    npm install react-native-screens react-native-safe-area-context
    ```
        
    For Icons Refrence , you can use:-
    
    https://oblador.github.io/react-native-vector-icons/

    2. Now in android android/app/build.gradle and add this
    
    ```gradle
    apply from: file("../../node_modules/react-native-vector-icons/fonts.gradle")
    ````



2. React Navigation 
   
   Here is the link for the docs

   https://reactnavigation.org/docs/getting-started
    ```bash
    npm install @react-navigation/native
    ```

    In src/App.js, import this

    ```js
    import { NavigationContainer } from '@react-navigation/native';
    ```

    1. We will use React Native Bottom Tabs Navigator for  

        Read docs:-

        https://reactnavigation.org/docs/bottom-tab-navigator/

        ```bash
        npm install @react-navigation/bottom-tabs
        ```

        ```jsx
        import { View, Text } from 'react-native'
        import React from 'react'
        import '../global.css'
        import Icon from 'react-native-vector-icons/FontAwesome'
        import { NavigationContainer } from '@react-navigation/native';
        import { createBottomTabNavigator } from '@react-navigation/bottom-tabs'

        import Home from './screens/Home'
        import Profile from './screens/Profile';


        const BottomTab= createBottomTabNavigator()

        const BottomTabNavigator=()=>{
        return(
            <BottomTab.Navigator
            screenOptions={{
                tabBarActiveTintColor: '#0066ff',
                tabBarInactiveTintColor: 'gray',
                tabBarStyle: {
                paddingBottom: 5,
                paddingTop: 5
                }
            }}
            >
            <BottomTab.Screen 
            name="Home" 
            component={Home}
            options={{
                tabBarIcon:({color})=>(
                <Icon name='home' color={color} size={24}/>
                )
            
            }}  
            />
            <BottomTab.Screen 
            name="Profile" 
            component={Profile}
            options={{
                tabBarIcon:({color})=>(
                <Icon name='user' color={color} size={24}/>
                )
            }}
            />
            </BottomTab.Navigator>
        )
        }


        const App = () => {
        return (
            <NavigationContainer>
            <BottomTabNavigator/>
            </NavigationContainer>
        )
        }

        export default App
        ```