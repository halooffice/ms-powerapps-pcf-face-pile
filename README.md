# Setup

https://learn.microsoft.com/zh-cn/training/modules/build-power-app-component/

```sh
# pcf init --namespace Learn --name ReactFacePile --template field --framework React
npm install

# // ReactFacePile/ControlManifest.Input.xml
# // <property name="numberOfFaces" display-name-key="numberOfFaces_Display_Key" description-key="numberOfFaces_Desc_Key" of-type="Whole.None" usage="bound" required="false" />

# mkdir ReactFacePile/components
# git clone https://github.com/MicrosoftDocs/mslearn-developer-tools-power-platform
# cp power-apps-component-framework/FacePileComponent/FacePileComponent/Facepile.tsx ReactFacePile/components
# cp power-apps-component-framework/FacePileComponent/FacePileComponent/FacepileExampleData.ts ReactFacePile/components

# // Index.ts
# #import { HelloWorld, IHelloWorldProps } from "./HelloWorld";
# import { FacepileBasicExample, IFacepileBasicExampleProps } from "./components/Facepile" ;
# const DEFAULT_NUMBER_OF_FACES = 3;
# private props: IFacepileBasicExampleProps = {
#     numberFacesChanged: this.numberFacesChanged.bind(this),
# };

# // init
# this.props.numberOfFaces = context.parameters.numberOfFaces.raw || DEFAULT_NUMBER_OF_FACES;

# // updateView
# public updateView(context: ComponentFramework.Context<IInputs>): React.ReactElement {
#     if (context.updatedProperties.indexOf("numberOfFaces") > -1) {
#         this.props.numberOfFaces = context.parameters.numberOfFaces.raw || DEFAULT_NUMBER_OF_FACES;
#     }
#     return React.createElement(FacepileBasicExample, this.props);
# }

# // getOutputs
# public getOutputs(): IOutputs {
#     return {
#         numberOfFaces: this.props.numberOfFaces,
#     };
# }

# // add numberFacesChanged
# private numberFacesChanged(newValue: number) {
#     if (this.props.numberOfFaces !== newValue) {
#         this.props.numberOfFaces = newValue;
#         this.notifyOutputChanged();
#     }
# }

# mkdir ReactFacePile/css
# cp ReactFacePile.css ReactFacePile/css/
# mkdir ReactFacePile/strings
# cp power-apps-component-framework/FacePileComponent/FacePileStrings/ReactFacePile.1033.resx ReactFacePile/strings

npm run build
npm start
```