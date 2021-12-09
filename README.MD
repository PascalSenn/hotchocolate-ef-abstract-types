
## Example of how [HotChocolate](https://chillicream.com) works together in EntityFramewore Core  and abstract types

1. `dotnet run`
2. open `https://localhost:5000/graphql`
3. Execute the following query:
```graphql
{
   books(where: {title: {contains:"In"}}){
      nodes {
          title
      }
   }
  publications {
    nodes {
      id
      title
      __typename
      ... on Book {
        author {
          id
          name
        }
      }
      ... on Ebook {
        reader {
          name
        }
      }
      ... on Magazine {
        schedule
      }
      ... on Paper {
        fieldOfResearch
      }
    }
  }
}
```