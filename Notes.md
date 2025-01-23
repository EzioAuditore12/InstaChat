# Setting Up this Project

## Package used for navigation

1. For Icons in UI, we are using React-native-vector-icons

    1. Install The package
    ```bash
    npm install --save react-native-vector-icons
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
    npm install react-native-screens react-native-safe-area-context
    ```

    In src/App.js, import this

    ```js
    import { NavigationContainer } from '@react-navigation/native';
    ```

    Usecase,eg:-

    ```js
    const demo = () => {
    return (
    <NavigationContainer>
      {/*Here you have to write navigation type you are using in it */}
    </NavigationContainer>
    );
    };
    ```
   3. We have to create multiple screens inside src/screens

    ```bash
    touch 01_Home.jsx 02_Profile.jsx 03_Reel.jsx
    ```

    4. We will use React Native Bottom Tabs Navigator for  

        Read docs:-

        https://reactnavigation.org/docs/bottom-tab-navigator/

        ```bash
        npm install @react-navigation/bottom-tabs
        ```
         1. Import the bottom-tabs 
        ```jsx
        import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
        ```
         2. To use it Store it in a variable
        ```jsx
        const BottomTab = createBottomTabNavigator();
        ```

        1. We are using it here for switching between different screens i.e Home,Profile,Reel

            Usecase is here
            Here, you can see different styling you can use anyone , you can read this docs for more info

            https://reactnavigation.org/docs/status-bar
        ```jsx
        const BottomTabNavigator = () => {
        return (
        <BottomTab.Navigator
        screenOptions={{
            tabBarActiveTintColor: '#0066ff',
            tabBarInactiveTintColor: 'gray',
            tabBarStyle: {
            paddingVertical: 5,
            },
        }}
        >
        <BottomTab.Screen
            name="Home"
            component={Home}
            options={{
            tabBarIcon: ({ color }) => (
                <Icon name="home" color={color} size={24} />
            ),
            headerStyle: { backgroundColor: '#3b82f6' },
            headerTitleStyle: { color: 'white' },
            headerTitle:'InstaChat'
            }}
        />
        <BottomTab.Screen
            name="Profile"
            component={Profile}
            options={{
            tabBarIcon: ({ color }) => (
                <Icon name="user" color={color} size={24} />
            ),
            }}
        />
        <BottomTab.Screen
            name="Reel"
            component={Reel}
            options={{
            tabBarIcon: ({ color }) => (
                <Icon name="film" color={color} size={24} />
            ),
            }}
        />
        </BottomTab.Navigator>
        );
        };

        ```
    5. Now wrap bottomNavigator inside NavigationContainer
    
    ```jsx
    const App = () => {
    return (
    <NavigationContainer>
      <BottomTabNavigator />
    </NavigationContainer>
    );
    };

    ```