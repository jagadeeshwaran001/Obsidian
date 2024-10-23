In [[React]] useEffect is best suit to perform the side effects.

we can make a in-pure fuction into [[Pure function]] using [[useEffect]]

The [[useEffect]] has two argument

First is a [[callBack function]] to execute.
second is a dependency array, the fuction in first args run only if the dependency array value chages.

The code you place inside the useEffect hook always runs after your component mounts or, in other words, after React has updated the [[DOM]].

using return in [[useEffect]] will run the piece of code while component un-mount.