//Não é html > Não um site é o codigo de um app calculadora, você tem liberdade para dar forks ;)
///////////////////////////////////////////////////////////////////////////////////////////////////
///////////////////////////////////////////////////////////////////////////////////////////////////
///////////////////////////////////////////////////////////////////////////////////////////////////

import { StatusBar } from 'expo-status-bar';
import React, {useEffect, useState} from 'react';
import { StyleSheet, Text, View, Botão, ProgressViewIOSComponent, TouchableHighlight, TouchableOpacity } from 'react-native';



export default function App() {
///////////////////////////////////////////////////////////////////////////////////////////////////

  console.disableYellowBox = true;
  const [firstNumber, setfirstNumber] = useState(0);
  const [secondeNumber, sesecondeNumber] = useState(0);
  const [sinal, seSinal] = useState("");
  const [stringCalculo, setstringCalculo] = useState(0);
 
  var numeros = [];
  for (var i = 0; i <= 9; i++){
    numeros.push(i);
  }
 
  ///////////////////////////////////////////////////////////////////////////////////////////////////
//Botão
  export default function Botão(props){

  return(
  <View style={{backgroundColor:'black', borderColor:'white', borderWidth:1, width:'33.3%', height:'25%'}}>
    <TouchableOpacity onPress={()=>props.logicaCalculadora(props.numero)} style={{width:'100%', height:'100%', justifyContent:'center', alignItems:'center'}}>
      <Text style={{fontSize:24, color:'white'}}>{props.numero}</Text>
    </TouchableOpacity>
  </View>
  
  )}

  ///////////////////////////////////////////////////////////////////////////////////////////////////
//Funções de Calculculo;

  function logicaCalculadora(n){
    if(sinal == ""){
      setfirstNumber(parseInt(firstNumber.toString() + n.toString()))
      setstringCalculo(parseInt(firstNumber.toString() + n.toString()))
    }
    if((n == "+" || n == "-" || n == "x" || n == "/") && secondeNumber == 0){
      setstringCalculo(firstNumber.toString() + n);
      setsinal(n);
    }
    if(sinal != ""){
      setsecondenumber(parseInt(secondeNumber.toString() + n.toString()))
      setstringCalculo(firstNumber+sinal+parseInt(secondeNumber.toString() + n.toString()))
    }
    if(n == "="){
      let resultado = 0;
      if(sinal == "+"){
        resultado = firstNumber+secondeNumber;
      }else if(sinal == "/"){
        resultado = firstNumber/secondeNumber;
      }
      else if(sinal == "-"){
        resultado = firstNumber-secondeNumber;
      }
      else if(sinal == "*"){
        resultado = firstNumber*secondeNumber;
      }
      setstringCalculo(resultado);
      setsinal("");
      setfirstNumber(resulatado);
      setsecondenumber(0);
    }
  }

  ///////////////////////////////////////////////////////////////////////////////////////////////////

  return (
    <View style={{flex:1, backgroundColor:'black'}}>

      <StatusBar hidden />

  ///////////////////////////////////////////////////////////////////////////////////////////////////
  //Sinais:

     <View style={style.boxnumber}><Text style={{fontSize:30, color:'white'}}>{stringCalculo}</Text></View>
     <View style={{flex:1,flexDirection:'row', height:'16.6', alignItems:'center'}}>
       <TouchableOpacity onPress={()=>logicaCalculadora('+')} style={style.botões}><Text style={{fontSize:27}}>+</Text></TouchableOpacity>
       <TouchableOpacity onPress={()=>logicaCalculadora('/')} style={style.botões}><Text style={{fontSize:27}}>/</Text></TouchableOpacity>
       <TouchableOpacity onPress={()=>logicaCalculadora('*')} style={style.botões}><Text style={{fontSize:27}}>*</Text></TouchableOpacity>
       <TouchableOpacity onPress={()=>logicaCalculadora('-')} style={style.botões}><Text style={{fontSize:27}}>-</Text></TouchableOpacity>
       <TouchableOpacity onPress={()=>logicaCalculadora('-')} style={style.botões}><Text style={{fontSize:27}}>=</Text></TouchableOpacity>
     </View>
     <View style={{flexDirection:'row', flexWrap:'wrap', borderTopColor:'black', borderTopWidth:2, height:'66.8%'}}>
       {numeos.map(function(e){return(<Botão logicaCalculadora={logicaCalculadora} numero={e}></Botão>)})}</View>
    </View>
  );
}

///////////////////////////////////////////////////////////////////////////////////////////////////

const styles = StyleSheet.create({
  boxnumber:{padding:10, borderBottomWidth:2, height:20, justifyContent:'center', paddingLeft:27},
  botões:{width:'25%', backgroundColor:'black', justifyContent:'center', alignItems:'center', height:'100%'}
});
